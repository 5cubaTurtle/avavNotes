[stl vs std](https://stackoverflow.com/a/5205571/24231920)

**Containers:**
Every type that is a model of Container has an associated [[iterators|iterator]] type with which to iterate through the container's elements.

A containers "owns" its elements: the lifetime of an element stored in a container cannot exceed that of the container itself. Meaning container stores values, not ptrs to data.
