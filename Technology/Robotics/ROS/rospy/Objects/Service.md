[guide](http://wiki.ros.org/ROS/Tutorials/WritingServiceClient%28python%29)
### server example
```python
#!/usr/bin/env python
from __future__ import print_function
from beginner_tutorials.srv import AddTwoInts,AddTwoIntsResponse
import rospy
def handle_add_two_ints(req):
    print("Returning [%s + %s = %s]"%(req.a, req.b, (req.a + req.b)))
    return AddTwoIntsResponse(req.a + req.b)
def add_two_ints_server():
    rospy.init_node('add_two_ints_server')
    s = rospy.Service('add_two_ints', AddTwoInts, handle_add_two_ints)
    print("Ready to add two ints.")
    rospy.spin()
if __name__ == "__main__":
    add_two_ints_server()
```
#### Creating the service explanation:
```python
from beginner_tutorials.srv import AddTwoInts
s = rospy.Service('add_two_ints', AddTwoInts, handle_add_two_ints)
```
This declares a new service named `'add_two_ints'` with the `AddTwoInts` service type. All requests are passed to `handle_add_two_ints` function. `handle_add_two_ints` is called with instances of `AddTwoIntsRequest` and returns instances of `AddTwoIntsResponse`.
#### service callback:
Example:
```python
from beginner_tutorials.srv import AddTwoIntsResponse
def handle_add_two_ints(req):
    print("Returning [%s + %s = %s]"%(req.a, req.b, (req.a + req.b)))
    return AddTwoIntsResponse(req.a + req.b)
```

### client example
```python
#!/usr/bin/env python
from __future__ import print_function
import sys
import rospy
from beginner_tutorials.srv import *
def add_two_ints_client(x, y):
    rospy.wait_for_service('add_two_ints')
    try:
        add_two_ints = rospy.ServiceProxy('add_two_ints', AddTwoInts)
        resp1 = add_two_ints(x, y)
        return resp1.sum
    except rospy.ServiceException as e:
        print("Service call failed: %s"%e)
def usage():
    return "%s [x y]"%sys.argv[0]
if __name__ == "__main__":
    if len(sys.argv) == 3:
        x = int(sys.argv[1])
        y = int(sys.argv[2])
    else:
        print(usage())
        sys.exit(1)
    print("Requesting %s+%s"%(x, y))
    print("%s + %s = %s"%(x, y, add_two_ints_client(x, y)))
```
For clients you don't have to call init_node().
- `rospy.wait_for_service('add_two_ints')` is a convenience method that blocks until the service named `add_two_ints` is available.
- `add_two_ints = rospy.ServiceProxy('add_two_ints', AddTwoInts)` Creates a callable function.