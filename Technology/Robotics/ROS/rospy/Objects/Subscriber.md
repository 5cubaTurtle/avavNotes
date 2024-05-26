Listen to a [[Topic]]
```python
def callback(msg):
	print("I got:", msg.data)

rospy.Subscriber("chatter", String, callback)
```
This line will register a `callback` to be called for each new message on the topic `"chatter"`.
