Establish rosnode and send a message with a timestamp:
```python
import rospy
from std_msgs.msg import Header
from your_package.msg import YourMessageType

rospy.init_node('your_node')

pub = rospy.Publisher('your_topic', YourMessageType, queue_size=10)

while not rospy.is_shutdown():
    msg = YourMessageType()

    # Set message data here

    header = Header()
    header.stamp = rospy.Time.now()
    msg.header = header
    pub.publish(msg)
    rospy.sleep(1)
```

Get the data from *Int32MultiArray* or (any other type apparently):
```python
import rospy
from std_msgs.msg import Int32MultiArray

def callback(msg):
    data = msg.data
    # Process the data here
    print(data)

rospy.init_node('your_node')
sub = rospy.Subscriber('your_topic', Int32MultiArray, callback)
rospy.spin() # wait for incoming messages
```