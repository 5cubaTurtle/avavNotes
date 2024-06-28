#networking 

Static routing involves manually adding IP routes to the system’s routing table, and this is usually done by manipulating the routing table with the [[route]] command. 
Static routing enjoys many advantages over dynamic routing: 
- simplicity of implementation on smaller networks
- predictability (the routing table is always computed in advance, and thus the route is precisely the same each time it is used)
- low overhead on other routers and network links due to the lack of a dynamic routing protocol.
However, static routing does present some disadvantages as well. For example, static routing is limited to small networks and does not scale well. Static routing also fails completely to adapt to network outages and failures along the route due to the fixed nature of the route.