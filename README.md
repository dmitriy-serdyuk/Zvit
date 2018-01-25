# Звіт / Zvit

## Fast User Guide:

Creating a logger object: 
```python
ZvitWriter(logDir, step, flushSecs=5.0)
```
Making it the default for a scope: `with ... as ...:`
Logging with explicit `ZvitWriter`: `z.logScalar()`
Logging with implicit, current default `ZvitWriter`: `logScalar()`
Getting current default `ZvitWriter`: `topZvit()`
Logging functions: `logScalar`, `logImage`, `logAudio`, `logTensor`, `logText`, `logHist`, `logMessage`, `logSession`, `logLayout`
Tag name scoping: 
```python
with [z.]tagscope("sub", "sub", "scope"):
    ...
```
Chaining methods: `topZvit().logScalar("foo", 42).logScalar("bar", 44)`
Stepping the logger one global step #: `topZvit().step()`   (Important: Do this after every training step!!!!!!!)
Flushing: `topZvit().flush()`
Closing: `topZvit().close()`

Nota Bene: `topZvit()` and all the `log*()` functions work even outside a `with ZvitLogger(...) as z` scope, but they discard everything they receive and act as a noop. That's for convenience purposes, to allow logging to be easily disabled.
