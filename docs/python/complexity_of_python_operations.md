# 파이썬 시간복잡도

## 자료형 별 시간 복잡도

### list

|Operation     | Example      | Class         |
|--------------|--------------|---------------|
|Index         | l[i]         | O(1)	      |
|Store         | l[i] = 0     | O(1)	      |
|Length        | len(l)       | O(1)	      |
|Append        | l.append(5)  | O(1)	      |
|Pop	       | l.pop()      | O(1)	      |
|Clear         | l.clear()    | O(1)	      |
|Slice         | l[a:b]       | O(b-a)	      |
|Extend        | l.extend(...)| O(len(...))   |
|Construction  | list(...)    | O(len(...))   |
|check ==, !=  | l1 == l2     | O(N)          |
|Insert        | l[a:b] = ... | O(N)	      |
|Delete        | del l[i]     | O(N)	      |
|Containment   | x in/not in l| O(N)	      |
|Copy          | l.copy()     | O(N)	      |
|Remove        | l.remove(...)| O(N)	      | 
|Pop	       | l.pop(i)     | O(N)	      |
|Extreme value | min(l)/max(l)| O(N)          |
|Reverse	   | l.reverse()  | O(N)	      |
|Iteration     | for v in l:  | O(N)          |
|Sort          | l.sort()     | O(N Log N)    |
|Multiply      | k*l          | O(k N)        |

### set

|Operation     | Example      | Class         |
|--------------|--------------|---------------|
|Length        | len(s)       | O(1)	     |
|Add           | s.add(5)     | O(1)	     |
|Containment   | x in/not in s| O(1)	     |
|Remove        | s.remove(..) | O(1)	     |
|Discard       | s.discard(..)| O(1)	     | 
|Pop           | s.pop()      | O(1)	     |
|Clear         | s.clear()    | O(1)	     |
|Construction  | set(...)     | O(len(...))   |
|check ==, !=  | s != t       | O(len(s))     |
|<=/<          | s <= t       | O(len(s))     |
|>=/>          | s >= t       | O(len(t))     |
|Union         | s | t        | O(len(s)+len(t))|
|Intersection  | s & t        | O(len(s)+len(t))|
|Difference    | s - t        | O(len(s)+len(t))|
|Symmetric Diff| s ^ t        | O(len(s)+len(t))|
|Iteration     | for v in s:  | O(N)          |
|Copy          | s.copy()     | O(N)	     |

### dictionary

|Operation     | Example      | Class         |
|--------------|--------------|---------------|
|Index         | d[k]         | O(1)	     |
|Store         | d[k] = v     | O(1)	     |
|Length        | len(d)       | O(1)	     |
|Delete        | del d[k]     | O(1)	     |
|get/setdefault| d.get(k)     | O(1)	     |
|Pop           | d.pop(k)     | O(1)	     | 
|Pop item      | d.popitem()  | O(1)	     |
|Clear         | d.clear()    | O(1)	     |
|View          | d.keys()     | O(1)	     |
|Construction  | dict(...)    | O(len(...))   |
|Iteration     | for k in d:  | O(N)          |
