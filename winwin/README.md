# WinWin
## Window event management system

Throttles window event bindings via requestAnimationFrame.

### Dependencies
Requires jQuery

### Usage

```
WinWin.start();

WinWin.bind('scroll', yourHandlingFunction);
WinWin.unbind('scroll');
```

But what if you want to bind multiples, and maybe unbind one later?

```
WinWin.bind('scroll', scrollFnc, 'my-scroll'); // 'my-scroll' is the binding reference/name
WinWin.bind('scroll', otherScrollFnc, 'my-other-scroll');
WinWin.unbind('my-scroll');
// my-other-scroll still fires
```

Okay, but what if something is already bound to that reference/name?

```
WinWin.bind('scroll', scrollFnc, 'my-binding-name');
WinWin.bind('resize', resizeFnc, 'my-binding-name');
WinWin.unbind('my-binding-name');
// nothing fires
```

BUT! Keep in mind these references are JUST references in name only, and dont act as actual bindings.
For instance:

```
WinWin.bind('scroll', scrollFnc, 'my-binding-name');
WinWin.bind('resize', resizeFnc, 'my-binding-name');
WinWin.unbind('scroll');
// resizeFnc still fires
```


There are also some functions to control WinWin's monitoring:

```
WinWin.start();
WinWin.pause();
WinWin.resume();
WinWin.stop();
// Note that you do not need to rebind functions - this merely affects the polling.
```

### List of Available Functions

```
WinWin.bind('scroll', scrollFnc, 'my-binding-name');
WinWin.on('scroll', scrollFnc, 'my-binding-name');
WinWin.unbind('my-binding-name');

WinWin.unbind(); // alias for...
WinWin.unbindAll();

WinWin.start();
WinWin.pause();
WinWin.resume();
WinWin.stop();
```
