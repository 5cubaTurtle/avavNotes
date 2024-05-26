#python #multiprocessing 
Connection between 2 processes.

Two connection objects are produced by a [[Pipe]].
create two connections of a Pipe: `end_a, end_b = Pipe()`
send data:`end_a.send(data)`, receive data:`data = end_b.recv()` .