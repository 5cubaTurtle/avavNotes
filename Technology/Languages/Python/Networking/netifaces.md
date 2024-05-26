get all interfaces on the system:
```python
import netifaces  
interfaces = netifaces.interfaces()
```
get a [[dict]]ionary of addresses associated with and interface called *enp0s31f6*: ```
```python
addresses_dict = netifaces.ifaddresses('enp0s31f6')
```
get the [[Technology/Networking/Concepts/Protocols/IP|ip4]] of an interface:
```python
ip = netifaces.ifaddresses('enp0s31f6')[netifaces.AF_INET][0]['addr']
```
