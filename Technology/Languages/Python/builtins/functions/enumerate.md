```python
print("Available network interfaces:")  
for i, iface in enumerate(interfaces):
	addrs = netifaces.ifaddresses(iface)  
if netifaces.AF_INET in addrs:  
	ip = addrs[netifaces.AF_INET][0]['addr']  
	print(f"{i + 1}: {iface} ({ip})")  
else:  
	print(f"{i + 1}: {iface}")
```