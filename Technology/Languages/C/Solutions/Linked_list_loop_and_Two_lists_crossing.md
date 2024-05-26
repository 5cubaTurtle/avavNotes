
### Finding a loop in a linked-list
To find a loop in a linked list (i.e. a certain node in the list points to a previous node in the list): 

From the head of the list, send two iterators down the list. Advancing one of them in steps of one node and advancing the other in steps of two nodes. If the list is looped, the iterators will eventually meet one node before the loop (i.e. the following node will point to a previous node).

### Finding at which node two linked-lists meet
To determine if the two lists cross, check if their end nodes are the same. To fine the node at which they cross:
1. Find the length of both lists.
2. Then promote the iterator of the longer list number of times equal to the difference between their lengths. This will align the iterator's distance from the last node.
3. Then simply check to see if the two iterators are on the same node and if not promote them one node ahead until they find the merging node.
