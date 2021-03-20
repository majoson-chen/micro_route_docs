# Four ways of working
`micro_Route` works in four ways:

|Block\Thread|Single Thread         |Multithread              |
| :-------: | :-------------: | :-------------: |
|Blocking    |Single-Thread-Blocking|Multithread-Blocking     |
|Non-Blocking|Single-Thread-Non-Blocking|Multi-Thread-Non-Blocking|

## Blocking
The blocking option is used to set when executing `app.run()` Whether or not the main thread is stuck and does not return, if you set it to block, then The code you put after `app.run ()` may never run, which gives `micro_route` provides a stable working environment.

If you set it to non-blocking, that is, when you call `app.run()` after that, the program will return immediately so that the code you put after the `app.run` can be run.

and if you set it to non-blocking, the program you are working on may be interrupted when the browser makes a `socket' request.

## Threads
In some development baord, `micropython` does not support it to `multithreading`, which also means you cannot use it.

If your development baord supports multiple threads, you might consider turning on multiple threads to speed up multiple-request access.

How do I set how it works? [See here](./library/micro_route.html/#func-run-)