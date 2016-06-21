While developing Spyder it may happen that it freezes or hangs for some reason. Spyder is a multithreaded application, and has the ability to execute and control things in a separate process. Spyder communicates with other threads/processes using network sockets (`bsdsocket.py`), and if communication fails for some reason, it may enter an endless loop waiting for the input.

Here is an **example session with gdb on Fedora Linux** how to see what Spyder threads are doing during deadlock. Gdb on Fedora 16+ contains Python tools that may not be present on other systems. This assumes that you've executed Spyder with `gdb`. For development, it is convenient to run Spyder directly from source:

    gdb -ex r --args python bootstrap.py

Do whatever you do in Spyder to cause a deadlock, switch to `gdb` and interrupt the process with `Ctrl-C`.

    ^C
    Program received signal SIGINT, Interrupt.
    0xb7fff424 in __kernel_vsyscall ()
    (gdb)

Now inspect threads and look what do they do:

    (gdb) info threads
      Id   Target Id         Frame 
      29   Thread 0xa72fab40 (LWP 22636) "python" 0xb7fff424 in __kernel_vsyscall ()
      28   Thread 0xa7afbb40 (LWP 22635) "python" 0xb7fff424 in __kernel_vsyscall ()
      27   Thread 0xa82fcb40 (LWP 22634) "python" 0xb7fff424 in __kernel_vsyscall ()
      26   Thread 0xa8afdb40 (LWP 22633) "python" 0xb7fff424 in __kernel_vsyscall ()
      25   Thread 0xa92feb40 (LWP 22632) "python" 0xb7fff424 in __kernel_vsyscall ()
      24   Thread 0xa9affb40 (LWP 22631) "python" 0xb7fff424 in __kernel_vsyscall ()
      21   Thread 0xab036b40 (LWP 22628) "python" 0xb7fff424 in __kernel_vsyscall ()
      20   Thread 0xaa6ffb40 (LWP 22627) "python" 0xb7fff424 in __kernel_vsyscall ()
      3    Thread 0xabe18b40 (LWP 22610) "python" 0xb7fff424 in __kernel_vsyscall ()
      2    Thread 0xac741b40 (LWP 22609) "python" 0xb7fff424 in __kernel_vsyscall ()
    * 1    Thread 0xb7fdf6c0 (LWP 22605) "python" 0xb7fff424 in __kernel_vsyscall ()
    (gdb) py-list
     109    # See solution (1) in Issue 434:
     110    # http://code.google.com/p/spyderlib/issues/detail?id=434#c13
     111    def communicate(sock, command, settings=[]):
     112        """Communicate with monitor"""
     113        try:
    >114            COMMUNICATE_LOCK.acquire()
     115            write_packet(sock, command)
     116            for option in settings:
     117                write_packet(sock, option)
     118            return read_packet(sock)
     119        finally:
    (gdb) thread 29
    [Switching to thread 29 (Thread 0xa72fab40 (LWP 22636))]
    #0  0xb7fff424 in __kernel_vsyscall ()
    (gdb) py-list
    Unable to locate python frame
    (gdb) thread 28
    [Switching to thread 28 (Thread 0xa7afbb40 (LWP 22635))]
    #0  0xb7fff424 in __kernel_vsyscall ()
    (gdb) py-list
     197            for method in _delegate_methods:
     198                setattr(self, method, dummy)
     199        close.__doc__ = _realsocket.close.__doc__
     200    
     201        def accept(self):
    >202            sock, addr = self._sock.accept()
     203            return _socketobject(_sock=sock), addr
     204        accept.__doc__ = _realsocket.accept.__doc__
     205    
     206        def dup(self):
     207            """dup() -> socket object
    (gdb)

Do this for all threads to get a picture of what's going on. There is a shortcut for it:

    (gdb) t a a py-list

Which means `thread apply all py-list`.

In my case there was a blocking read on a socket in Thread 27:
```
(gdb) thread 27
[Switching to thread 27 (Thread 0xa82fcb40 (LWP 22634))]
#0  0xb7fff424 in __kernel_vsyscall ()
(gdb) py-list
  69            prefix = "R%02d.%02d" % (sock.fileno(), read_counter)
  70            logfile.write("%s " % (prefix))
  71        sock.settimeout(timeout)
  72        dlen, data = None, None
  73        try:
 >74            datalen = sock.recv(SZ)
  75            if DEBUG:
  76                logfile.write("len(len):%s\n" % (len(datalen)))
  77            dlen, = struct.unpack("l", datalen)
  78            if DEBUG:
  79                logfile.write("%s   (%s) " % (prefix, dlen))
(gdb)
```
You can then use `py-up` and `py-down` commands to walk through the stack in each thread, or use `py-bt` to dump the full (and a bit too verbose) stack trace.

Enjoy hacking.

P.S. If you know how to improve this technique, please, post a note to Spyder discussion group and add me (techtonik@gmail.com) to CC. Thanks.

P.P.S. And thanks to Fedora hackers for awesome tools http://fedoraproject.org/wiki/Features/EasierPythonDebugging 