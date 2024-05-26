publish the message type *String* to the [[Topic]] `'chatter'`:
```python
from std_msgs.msg import String
pub = rospy.Publisher('chatter', String, queue_size=10)
# ... some code ... #
pub.publish(the_message)
```
The `queue_size` argument limits the amount of queued messages if any subscriber is not receiving them fast enough. The `publish` method of the `Publisher` class does the actual publishing to the topic.