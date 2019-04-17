# csci4210-hw4-client
Python 3 client library for OpSys HW4, Spring 2019

* Supports SHARE (reads from a bytestring or file object, writes to a bytestring).
* Uses a user-supplied callback function to handle incoming messages.
* I've found that if you send a message to yourself (either SEND or BROADCAST), you get both the OK!\n response and the message in the same recv call.
  Not necessarily a huge problem, but if anyone has any ideas on how to fix it, I'd appreciate a PR or something.

Example usage:
```python
import clientlib
c = clientlib.Client(lambda *args: print("{:s} {:s}: {!r:s}".format(*args)), port)
c.login("user1")
c.send("user2", b"hello!\n")
c.close()
```
