### treq
---
https://github.com/twisted/treq

```py
// src/treq/local_httpbin/test/test_parent.py

skip = skip_on_window_because_of_199()

@attr.s
class FakeProcessTransportState(object):
  
  standard_in_closed = attr.ib(default=False)
  standard_out_closed = attr.ib(default=False)
  standard_error_closed = attr.ib(default=False)
  signals = attr.ib(default=attr.Factory(list))
  
@implementer(IProcessTransport)
@attr.s
class FakeProcessTransport(StringTransport, object):
  
  pid = 1234
  
  _state = attr.ib()
  
  def closeStdin(self):
    self._state.standard_in_closed = True
  
  def closeStdout(self):
    self._state.standard_out_closed = True
    
  def closeStderr(self):
    self._state.standard_error_closed = True
  
  def closeChildFD(self, descriptor):
    
  def writeToChild(self, childFD, data):
    
  def signalProcess(self, signalID):
    self._state.signals.append(signalID)
  
class FakeProcessTransportTests(SynchronousTestCase):
  
  def setUp(self):
    self.state = FakeProcessTransportState()
    self.transport = FakeProcessTransport(self.state)
    
  def test_provides_interface(self):
    verify.verifyObject(IProcessTransport, self.transport)
  
  def test_closeStdin(self):
    self.assertFalse(self.state.standard_in_closed)
    self.transport.closeStdin()
    self.assertTrue(self.state.standard_in_closed)
  
  def test_closeStdout(self):


class HTTPServerProcessProtocolTests(SynchronousTestCase):
  
  def setUp(self):
  
  def assertStandardInputAndOutputClosed(self):
  
  def test_received_http_description(self):
 
@attr.s
class SpawnedProcess(object):

  process_protocol = attr.ib()
  executable = attr.ib()
  args = attr.ib()
  env = attr.ib()
  
  def send_stdout(self, data):
  
  def end_process(self, reason):
  
@implementer(IReactorCore, IReactorProcess):
class MemoryProcessReactor(MemoryReactor):

  def __init__(self):
    MemoryReactor.__init__(self)
    self.spawnedProcesses = []
    
  def spawnProcess(self, processProtocol, executable, args=(), env={},
      path=None, uid=None, gid=None, usePTY=0, childFDs=None):
      
    transport_state = FakeProcessTrasportState()
    transport = FakeProcessTransport(transport_state)
    
    self.spawnedProcesses.append(SpawnedProcess(
      process_protocol=processProtocol,
      executable=executable,
      args=args,
    ))
    
    processProtocol.makeConnection(transport)
    
    return transport
    
class MemoryProcessREactorTests(SynchronousTestCase):

  def test_provides_interfaces(self):
    reactor = MemoryProcessReactor()
    verify.verifyObject(IReactorCore, reactor)
    verify.verifyObject(IReactorProcess, reactor)
    
class HTTPBinProcessTests(SynchronousTestCase):

  def setUp():
  
  def fd_recording_open():
  
  def spawned_process():
  
  def assertSpawnAndDescription():




```

```
```

```
```


