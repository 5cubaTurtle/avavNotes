To ping a remote host using Python, you can use the ping3 library:
```python
import ping3

# Define the host to ping
host = "www.google.com"

# Send a ping request with a timeout of 1 second
response = ping3.ping(host, timeout=1)

# Check the response to see if the ping was successful
if response is not None:
    print(f"Ping to {host} successful")
else:
    print(f"Ping to {host} failed")
```
The method returns None if the ping request timed out or an integer representing the round-trip time of the ping in milliseconds if the request was successful.
