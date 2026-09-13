# Data Structure Interview Cheat Sheet: C++ vs C# vs Java vs Python3

A side-by-side reference for the most common data structures used in coding
interviews, with their main operations in each language.

---

## 1. Dynamic Array / List

| Operation            | C++ (`std::vector<T>`)     | C# (`List<T>`)              | Java (`ArrayList<T>`)         | Python3 (`list`)          |
|----------------------|-----------------------------|------------------------------|--------------------------------|---------------------------|
| Declare              | `vector<int> v;`            | `List<int> v = new();`       | `List<Integer> v = new ArrayList<>();` | `v = []`         |
| Add to end           | `v.push_back(x)`            | `v.Add(x)`                   | `v.add(x)`                     | `v.append(x)`             |
| Remove from end      | `v.pop_back()`              | `v.RemoveAt(v.Count-1)`      | `v.remove(v.size()-1)`         | `v.pop()`                 |
| Insert at index      | `v.insert(v.begin()+i, x)`  | `v.Insert(i, x)`              | `v.add(i, x)`                  | `v.insert(i, x)`          |
| Remove at index      | `v.erase(v.begin()+i)`      | `v.RemoveAt(i)`               | `v.remove(i)`                  | `del v[i]` / `v.pop(i)`   |
| Access by index      | `v[i]`                      | `v[i]`                        | `v.get(i)`                     | `v[i]`                    |
| Size                 | `v.size()`                  | `v.Count`                     | `v.size()`                     | `len(v)`                  |
| Contains             | `find(v.begin(),v.end(),x)!=v.end()` | `v.Contains(x)`      | `v.contains(x)`                 | `x in v`                  |
| Sort                 | `sort(v.begin(), v.end())`  | `v.Sort()`                    | `Collections.sort(v)`          | `v.sort()`                |
| Slice/Sub-range      | `vector<int>(v.begin()+i,v.begin()+j)` | `v.GetRange(i, len)` | `v.subList(i, j)`               | `v[i:j]`                  |
| Reverse              | `reverse(v.begin(), v.end())` | `v.Reverse()`               | `Collections.reverse(v)`       | `v.reverse()` / `v[::-1]` |

---

## 2. Stack (LIFO)

| Operation   | C++ (`std::stack<T>`) | C# (`Stack<T>`)     | Java (`Deque<T>` as stack)      | Python3 (`list`) |
|-------------|------------------------|----------------------|-----------------------------------|------------------|
| Declare     | `stack<int> s;`        | `Stack<int> s = new();` | `Deque<Integer> s = new ArrayDeque<>();` | `s = []`   |
| Push        | `s.push(x)`            | `s.Push(x)`          | `s.push(x)`                       | `s.append(x)`    |
| Pop         | `s.pop()` (void)       | `s.Pop()`            | `s.pop()`                         | `s.pop()`        |
| Top/Peek    | `s.top()`              | `s.Peek()`           | `s.peek()`                        | `s[-1]`          |
| Empty       | `s.empty()`            | `s.Count == 0`       | `s.isEmpty()`                     | `not s`          |
| Size        | `s.size()`             | `s.Count`            | `s.size()`                        | `len(s)`         |

> Note: Java's legacy `Stack` class exists but `ArrayDeque` is preferred (faster, non-synchronized).

---

## 3. Queue (FIFO)

| Operation   | C++ (`std::queue<T>`) | C# (`Queue<T>`)     | Java (`Queue<T>` / `ArrayDeque`)  | Python3 (`collections.deque`) |
|-------------|------------------------|----------------------|-----------------------------------|--------------------------------|
| Declare     | `queue<int> q;`        | `Queue<int> q = new();` | `Queue<Integer> q = new ArrayDeque<>();` | `q = deque()`         |
| Enqueue     | `q.push(x)`            | `q.Enqueue(x)`       | `q.offer(x)`                      | `q.append(x)`                  |
| Dequeue     | `q.pop()` (void)       | `q.Dequeue()`        | `q.poll()`                        | `q.popleft()`                  |
| Front       | `q.front()`            | `q.Peek()`           | `q.peek()`                        | `q[0]`                         |
| Empty       | `q.empty()`            | `q.Count == 0`       | `q.isEmpty()`                     | `not q`                        |
| Size        | `q.size()`             | `q.Count`            | `q.size()`                        | `len(q)`                       |

---

## 4. Deque (Double-Ended Queue)

| Operation       | C++ (`std::deque<T>`) | C# (`LinkedList<T>`)      | Java (`ArrayDeque<T>`)   | Python3 (`collections.deque`) |
|-----------------|-------------------------|-----------------------------|----------------------------|--------------------------------|
| Push front      | `d.push_front(x)`      | `d.AddFirst(x)`             | `d.addFirst(x)`            | `d.appendleft(x)`              |
| Push back       | `d.push_back(x)`       | `d.AddLast(x)`              | `d.addLast(x)`              | `d.append(x)`                  |
| Pop front       | `d.pop_front()`        | `d.RemoveFirst()`           | `d.pollFirst()`             | `d.popleft()`                  |
| Pop back        | `d.pop_back()`         | `d.RemoveLast()`            | `d.pollLast()`              | `d.pop()`                      |
| Peek front/back | `d.front()/d.back()`   | `d.First.Value/d.Last.Value`| `d.peekFirst()/peekLast()`  | `d[0]/d[-1]`                   |

---

## 5. Linked List

| Operation      | C++ (`std::list<T>`) | C# (`LinkedList<T>`)  | Java (`LinkedList<T>`)   | Python3 (no built-in; use `deque` or custom class) |
|----------------|------------------------|-------------------------|-----------------------------|------------------------------------------------------|
| Add front      | `l.push_front(x)`     | `l.AddFirst(x)`          | `l.addFirst(x)`             | `d.appendleft(x)`                                     |
| Add back       | `l.push_back(x)`      | `l.AddLast(x)`           | `l.addLast(x)`               | `d.append(x)`                                         |
| Remove         | `l.erase(it)`         | `l.Remove(node)`         | `l.remove(x)`                 | custom node manipulation                              |
| Traverse       | iterator `++it`       | `.Next` on `LinkedListNode` | `.getNext()` (custom) or iterator | `.next` pointer (custom class)                 |

> For interview problems ("reverse a linked list", "detect cycle"), all four languages typically require you to **define your own `Node`/`ListNode` class** rather than use the built-in list type.

---

## 6. Hash Map / Dictionary

| Operation         | C++ (`std::unordered_map<K,V>`) | C# (`Dictionary<K,V>`)      | Java (`HashMap<K,V>`)         | Python3 (`dict`)         |
|-------------------|-----------------------------------|-------------------------------|----------------------------------|---------------------------|
| Declare           | `unordered_map<string,int> m;`   | `Dictionary<string,int> m = new();` | `Map<String,Integer> m = new HashMap<>();` | `m = {}`        |
| Insert/Update     | `m[k] = v;`                      | `m[k] = v;`                    | `m.put(k, v);`                    | `m[k] = v`                |
| Get               | `m[k]` / `m.at(k)`               | `m[k]`                         | `m.get(k)`                        | `m[k]`                    |
| Get with default  | `m.count(k) ? m[k] : def`        | `m.GetValueOrDefault(k, def)`  | `m.getOrDefault(k, def)`          | `m.get(k, def)`           |
| Contains key      | `m.count(k)` / `m.contains(k)` (C++20) | `m.ContainsKey(k)`      | `m.containsKey(k)`                | `k in m`                  |
| Remove            | `m.erase(k)`                     | `m.Remove(k)`                  | `m.remove(k)`                     | `del m[k]` / `m.pop(k)`   |
| Iterate           | `for (auto& [k,v] : m)`          | `foreach (var kv in m)`        | `for (var e : m.entrySet())`      | `for k, v in m.items()`   |
| Size              | `m.size()`                       | `m.Count`                      | `m.size()`                        | `len(m)`                  |

> C++ also has `std::map` (ordered, O(log n), red-black tree) — see Ordered Map section below.

---

## 7. Hash Set / Set

| Operation      | C++ (`std::unordered_set<T>`) | C# (`HashSet<T>`)         | Java (`HashSet<T>`)      | Python3 (`set`)      |
|----------------|----------------------------------|-----------------------------|-----------------------------|-----------------------|
| Declare        | `unordered_set<int> s;`         | `HashSet<int> s = new();`   | `Set<Integer> s = new HashSet<>();` | `s = set()`  |
| Insert         | `s.insert(x)`                    | `s.Add(x)`                   | `s.add(x)`                   | `s.add(x)`             |
| Remove         | `s.erase(x)`                     | `s.Remove(x)`                | `s.remove(x)`                | `s.remove(x)` / `s.discard(x)` |
| Contains       | `s.count(x)` / `s.contains(x)`  | `s.Contains(x)`              | `s.contains(x)`              | `x in s`               |
| Size           | `s.size()`                       | `s.Count`                    | `s.size()`                   | `len(s)`               |
| Set ops (∪,∩,-)| manual / `<algorithm>` set_union etc. | `s.UnionWith/IntersectWith/ExceptWith` | `retainAll/addAll/removeAll` | `s | s2`, `s & s2`, `s - s2` |

---

## 8. Ordered Map / Sorted Structures

| Operation         | C++ (`std::map<K,V>`)   | C# (`SortedDictionary<K,V>`) | Java (`TreeMap<K,V>`)      | Python3 (no built-in; use `sortedcontainers.SortedDict`) |
|-------------------|---------------------------|--------------------------------|--------------------------------|-------------------------------------------------------------|
| Insert            | `m[k] = v;`                | `m[k] = v;`                     | `m.put(k, v);`                  | `sd[k] = v`                                                   |
| First / Last key  | `m.begin()->first` / `m.rbegin()->first` | `m.Keys.First()/Last()` | `m.firstKey()/lastKey()`        | `sd.keys()[0]` / `sd.keys()[-1]`                              |
| Floor / Ceiling   | `m.lower_bound(k)` variants | manual                        | `m.floorKey(k)/ceilingKey(k)`   | `sd.irange` / `bisect`                                        |
| Ordered iteration | `for (auto& [k,v] : m)` (sorted) | `foreach` (sorted)        | `for (var e : m.entrySet())` (sorted) | `for k in sd` (sorted)                                  |

---

## 9. Priority Queue / Heap

| Operation        | C++ (`std::priority_queue<T>`) | C# (`PriorityQueue<T,P>` .NET 6+) | Java (`PriorityQueue<T>`)        | Python3 (`heapq`)             |
|-------------------|-----------------------------------|---------------------------------------|-------------------------------------|----------------------------------|
| Declare (min-heap)| `priority_queue<int, vector<int>, greater<int>> pq;` | `PriorityQueue<T,int> pq = new();` | `PriorityQueue<Integer> pq = new PriorityQueue<>();` | `pq = []` (list used with heapq) |
| Declare (max-heap)| `priority_queue<int> pq;` (default) | negate priority | `new PriorityQueue<>(Collections.reverseOrder())` | negate values pushed |
| Push              | `pq.push(x)`                     | `pq.Enqueue(x, priority)`             | `pq.offer(x)`                        | `heapq.heappush(pq, x)`          |
| Pop (top)         | `pq.top(); pq.pop();`            | `pq.Dequeue()`                        | `pq.poll()`                          | `heapq.heappop(pq)`              |
| Peek              | `pq.top()`                       | `pq.Peek()`                           | `pq.peek()`                          | `pq[0]`                          |
| Size              | `pq.size()`                      | `pq.Count`                            | `pq.size()`                          | `len(pq)`                        |

---

## 10. String / StringBuilder

| Operation           | C++ (`std::string`)         | C# (`string` / `StringBuilder`) | Java (`String` / `StringBuilder`) | Python3 (`str` / list join) |
|---------------------|--------------------------------|------------------------------------|---------------------------------------|--------------------------------|
| Concatenate (loop)  | `s += c;` (or use `stringstream`) | `sb.Append(c);`                    | `sb.append(c);`                        | `parts.append(c)` then `"".join(parts)` |
| Substring           | `s.substr(i, len)`             | `s.Substring(i, len)`               | `s.substring(i, j)`                    | `s[i:j]`                        |
| Length              | `s.size()` / `s.length()`      | `s.Length`                          | `s.length()`                           | `len(s)`                        |
| Char at index       | `s[i]`                          | `s[i]`                              | `s.charAt(i)`                          | `s[i]`                          |
| Split               | manual / `stringstream`         | `s.Split(' ')`                      | `s.split(" ")`                         | `s.split(" ")`                  |
| Reverse             | `reverse(s.begin(), s.end())`   | `new string(s.Reverse().ToArray())` | `new StringBuilder(s).reverse()`       | `s[::-1]`                       |
| To char array       | `vector<char>(s.begin(),s.end())` | `s.ToCharArray()`                | `s.toCharArray()`                       | `list(s)`                       |
| Immutable?          | mutable (`std::string`)         | immutable (`string`), mutable (`StringBuilder`) | immutable (`String`), mutable (`StringBuilder`) | immutable |
| Upper / Lower       | `transform(s.begin(),s.end(),s.begin(),::toupper)` | `s.ToUpper()/s.ToLower()` | `s.toUpperCase()/s.toLowerCase()` | `s.upper()/s.lower()` |
| Trim whitespace     | manual (no built-in until C++20 `<ranges>`) | `s.Trim()/TrimStart()/TrimEnd()` | `s.strip()/trim()` (Java: `strip()` preferred) | `s.strip()/lstrip()/rstrip()` |
| Replace             | manual loop / regex `<regex>` | `s.Replace(old, new)`             | `s.replace(old, new)`                  | `s.replace(old, new)`           |
| Contains substring  | `s.find(sub) != string::npos` | `s.Contains(sub)`                 | `s.contains(sub)`                       | `sub in s`                      |
| Index of substring  | `s.find(sub)` (npos if none) | `s.IndexOf(sub)` (-1 if none)     | `s.indexOf(sub)` (-1 if none)           | `s.find(sub)` (-1 if none) / `s.index(sub)` (raises) |
| Starts / Ends with  | `s.starts_with(p)/ends_with(p)` (C++20) | `s.StartsWith(p)/EndsWith(p)` | `s.startsWith(p)/endsWith(p)`           | `s.startswith(p)/endswith(p)`   |
| Compare (equality)  | `s1 == s2`                     | `s1 == s2` / `s1.Equals(s2)`      | `s1.equals(s2)` (never `==`)            | `s1 == s2`                      |
| Compare (lexicographic) | `s1 < s2` / `s1.compare(s2)` | `string.Compare(s1, s2)` / `s1.CompareTo(s2)` | `s1.compareTo(s2)` | `s1 < s2` |
| Join list of strings | manual loop / `stringstream` | `string.Join(",", list)`          | `String.join(",", list)`               | `",".join(list)`                |
| Split with multiple delimiters | manual / `<regex>` | `s.Split(new[]{',',';'})`  | `s.split("[,;]")`                       | `re.split('[,;]', s)`           |
| Parse to int/double | `stoi(s)/stod(s)`             | `int.Parse(s)/double.Parse(s)`    | `Integer.parseInt(s)/Double.parseDouble(s)` | `int(s)/float(s)`          |
| Convert number to string | `to_string(x)`            | `x.ToString()`                    | `String.valueOf(x)/Integer.toString(x)` | `str(x)`                       |
| Format / interpolate | `sprintf`/`std::format` (C++20) | `$"{x} items"` / `string.Format` | `String.format("%d items", x)`         | `f"{x} items"`                  |
| Efficient concatenation in a loop | `s += piece;` (string is mutable, still O(n) amortized) | `StringBuilder sb; sb.Append(piece);` then `sb.ToString();` | `StringBuilder sb = new StringBuilder(); sb.append(piece);` then `sb.toString();` | `parts=[]; parts.append(piece)` then `"".join(parts)` (avoid `+=` in a loop) |
| Repeat string       | manual loop / `string(n, 'x')` for single char | `new string('x', n)` / `string.Concat(Enumerable.Repeat(s,n))` | `"x".repeat(n)` (Java 11+)        | `s * n`                         |
| Char <-> ASCII code | `(int)c` / `(char)i`          | `(int)c` / `(char)i`               | `(int)c` / `(char)i`                   | `ord(c)` / `chr(i)`             |
| Palindrome check    | `s == string(s.rbegin(), s.rend())` | `s == new string(s.Reverse().ToArray())` | `s.equals(new StringBuilder(s).reverse().toString())` | `s == s[::-1]`         |

---

## 11. Pair / Tuple

| Operation     | C++ (`std::pair<A,B>`)     | C# (`(A,B)` tuple / `Tuple<A,B>`) | Java (no built-in; use array/`Map.Entry`/record) | Python3 (`tuple`)   |
|---------------|------------------------------|--------------------------------------|-----------------------------------------------------|----------------------|
| Create         | `make_pair(a, b)` / `{a,b}`  | `(a, b)`                             | `new AbstractMap.SimpleEntry<>(a,b)` or `record`     | `(a, b)`              |
| Access first   | `p.first`                    | `p.Item1`                            | `p.getKey()`                                          | `p[0]`                |
| Access second  | `p.second`                   | `p.Item2`                            | `p.getValue()`                                        | `p[1]`                |

---

## 12. File & Text File Processing

| Operation                     | C++ (`<fstream>`)                                    | C# (`System.IO`)                                      | Java (`java.nio.file` / `java.io`)                         | Python3 (built-in `open`)               |
|--------------------------------|-------------------------------------------------------|----------------------------------------------------------|----------------------------------------------------------------|-------------------------------------------|
| Open for reading               | `ifstream in("file.txt");`                            | `StreamReader sr = new("file.txt");`                      | `BufferedReader br = Files.newBufferedReader(Path.of("file.txt"));` | `f = open("file.txt", "r")`         |
| Open for writing (overwrite)   | `ofstream out("file.txt");`                           | `StreamWriter sw = new("file.txt");`                       | `BufferedWriter bw = Files.newBufferedWriter(Path.of("file.txt"));` | `f = open("file.txt", "w")`         |
| Open for appending             | `ofstream out("file.txt", ios::app);`                 | `new StreamWriter("file.txt", append: true);`              | `Files.newBufferedWriter(path, StandardOpenOption.APPEND);`     | `f = open("file.txt", "a")`             |
| Read entire file as one string | `stringstream ss; ss << in.rdbuf(); string s = ss.str();` | `string s = File.ReadAllText("file.txt");`             | `String s = Files.readString(Path.of("file.txt"));`             | `s = f.read()` (or `Path.read_text()`)  |
| Read all lines into a list     | loop `getline(in, line)` and `push_back` into `vector<string>` | `string[] lines = File.ReadAllLines("file.txt");` | `List<String> lines = Files.readAllLines(Path.of("file.txt"));` | `lines = f.readlines()` / `f.read().splitlines()` |
| Read line by line (streaming)  | `string line; while (getline(in, line)) { ... }`      | `string line; while ((line = sr.ReadLine()) != null) { ... }` | `String line; while ((line = br.readLine()) != null) { ... }` | `for line in f:` (line keeps trailing `\n`) |
| Write a line                   | `out << line << "\n";`                                | `sw.WriteLine(line);`                                      | `bw.write(line); bw.newLine();`                                 | `f.write(line + "\n")`                  |
| Write all lines at once        | loop with `<<`                                        | `File.WriteAllLines("file.txt", lines);`                   | `Files.write(Path.of("file.txt"), lines);`                      | `f.writelines(lines)`                   |
| Check file exists              | `filesystem::exists("file.txt")` (C++17)              | `File.Exists("file.txt")`                                   | `Files.exists(Path.of("file.txt"))`                             | `os.path.exists("file.txt")` / `Path("file.txt").exists()` |
| Close file / auto-close        | closes on scope exit (RAII) or `in.close();`          | `using (var sr = new StreamReader(...)) { ... }`           | `try (var br = Files.newBufferedReader(path)) { ... }`          | `with open("file.txt") as f: ...`       |
| Split file into tokens/words   | `istringstream iss(line); string w; while (iss >> w) {...}` | `line.Split(' ')`                                     | `line.split("\\s+")`                                            | `line.split()`                          |
| Read CSV-like line             | manual split on `,`                                    | `line.Split(',')`                                           | `line.split(",")`                                               | `line.split(",")` or `csv` module       |
| Path join                      | `filesystem::path(dir) / "file.txt"` (C++17)          | `Path.Combine(dir, "file.txt")`                             | `Path.of(dir, "file.txt")`                                      | `os.path.join(dir, "file.txt")` / `Path(dir)/"file.txt"` |

**Typical "read file line-by-line and process" pattern:**

```cpp
// C++
ifstream in("file.txt");
string line;
while (getline(in, line)) {
    // process line
}
```

```csharp
// C#
foreach (var line in File.ReadLines("file.txt")) {
    // process line
}
```

```java
// Java
try (var br = Files.newBufferedReader(Path.of("file.txt"))) {
    String line;
    while ((line = br.readLine()) != null) {
        // process line
    }
}
```

```python
# Python3
with open("file.txt") as f:
    for line in f:
        line = line.rstrip("\n")
        # process line
```

> **Encoding tip:** Default text encoding differs by platform/language (C++ streams are byte-oriented by default; C# `StreamReader`/Java `Files.readString` default to UTF-8; Python3 `open()` uses the platform's locale-preferred encoding unless you pass `encoding="utf-8"` explicitly — always specify it for portability).

---

## 13. Time Complexity Quick Reference (same across all four languages)

| Structure            | Access   | Search   | Insert   | Delete   |
|-----------------------|----------|----------|----------|----------|
| Array/Vector/List      | O(1)     | O(n)     | O(n)*    | O(n)*    |
| Linked List            | O(n)     | O(n)     | O(1)**   | O(1)**   |
| Stack / Queue / Deque  | O(1) ends| O(n)     | O(1)     | O(1)     |
| Hash Map / Set         | -        | O(1) avg | O(1) avg | O(1) avg |
| Ordered Map (Tree)     | -        | O(log n) | O(log n) | O(log n) |
| Heap / Priority Queue  | O(1) top | O(n)     | O(log n) | O(log n) |

\* O(1) amortized at the end; O(n) for arbitrary index.
\** O(1) once you have the node reference; O(n) to find it first.

---

## 14. Operator & Language Construct Differences

Not every language supports the same operators/constructs. This section highlights where they **diverge** — critical to know so you don't write invalid code during an interview.

### 14.1 Increment / Decrement / Compound Assignment

| Feature                  | C++            | C#             | Java           | Python3                          |
|---------------------------|-----------------|-----------------|-----------------|------------------------------------|
| Pre-increment `++a`       | ✅ supported    | ✅ supported    | ✅ supported    | ❌ not supported (use `a += 1`)    |
| Post-increment `a++`      | ✅ supported    | ✅ supported    | ✅ supported    | ❌ not supported (use `a += 1`)    |
| Decrement `--a` / `a--`   | ✅ supported    | ✅ supported    | ✅ supported    | ❌ not supported (use `a -= 1`)    |
| Compound assign `+=,-=,*=,/=` | ✅          | ✅              | ✅              | ✅ (but no `++`/`--` versions)     |
| Bitwise compound `&=,|=,^=,<<=,>>=` | ✅    | ✅              | ✅              | ✅                                  |

> Python's design philosophy avoids `++`/`--` because `a++` in an expression is ambiguous/surprising (it doesn't even parse — `++a` is just unary-plus-unary-plus). Always use `a += 1`.

### 14.2 Ternary / Conditional Expression

| Language | Syntax                          |
|----------|----------------------------------|
| C++      | `cond ? a : b`                   |
| C#       | `cond ? a : b`                   |
| Java     | `cond ? a : b`                   |
| Python3  | `a if cond else b` (different order!) |

### 14.3 Logical Operators

| Feature        | C++          | C#           | Java         | Python3           |
|-----------------|--------------|--------------|--------------|--------------------|
| AND             | `&&`         | `&&`         | `&&`         | `and`              |
| OR              | `\|\|`       | `\|\|`       | `\|\|`       | `or`               |
| NOT             | `!`          | `!`          | `!`          | `not`              |
| Short-circuit?  | yes          | yes          | yes          | yes                |

### 14.4 Equality / Identity

| Feature                        | C++                     | C#                                 | Java                                     | Python3                          |
|----------------------------------|--------------------------|--------------------------------------|---------------------------------------------|-------------------------------------|
| Value equality (primitives)     | `==`                    | `==`                                 | `==`                                        | `==`                                |
| Value equality (objects/strings)| `==` (can be overloaded)| `==` (`string` overloads it to value equality) | `.equals()` — **`==` compares references!** | `==` (calls `__eq__`)              |
| Reference/identity equality     | pointer compare `p1==p2`| `object.ReferenceEquals(a,b)`        | `==` on non-primitive types                 | `is`                                |
| Not-equal                       | `!=`                    | `!=`                                 | `!=`                                        | `!=`                                |

> Biggest gotcha: **Java `String a == b` compares object references, not content** — must use `.equals()`. Python's `==` calls `__eq__`, correctly comparing content, but `is` checks identity (small int/string caching can make `is` misleadingly `True` for small values).

### 14.5 Division & Modulo

| Feature                         | C++                      | C#                        | Java                      | Python3                              |
|-----------------------------------|---------------------------|-----------------------------|-----------------------------|-----------------------------------------|
| Integer division                | `7 / 2` → `3` (truncates toward 0) | `7 / 2` → `3` (truncates toward 0) | `7 / 2` → `3` (truncates toward 0) | `7 // 2` → `3` (floors toward -∞) |
| True/float division             | `7.0 / 2` → `3.5`         | `7.0 / 2` → `3.5`          | `7.0 / 2` → `3.5`          | `7 / 2` → `3.5` (`/` is always float!)  |
| Modulo with negative operands    | `-7 % 2` → `-1` (sign follows dividend) | `-7 % 2` → `-1` | `-7 % 2` → `-1`            | `-7 % 2` → `1` (sign follows divisor)   |
| Power operator                  | ❌ none — use `pow(a,b)` / `<cmath>` | ❌ none — use `Math.Pow(a,b)` | ❌ none — use `Math.pow(a,b)` | ✅ `a ** b` built-in operator |

> This is a classic interview trap: **Python's `%` and `//` round toward negative infinity**, while C++/C#/Java round toward zero. `-7 % 3` is `2` in Python but `-1` in the other three.

### 14.6 Type System / Declarations

| Feature                  | C++                          | C#                          | Java                        | Python3                    |
|----------------------------|--------------------------------|--------------------------------|--------------------------------|-------------------------------|
| Static vs dynamic typing | static                        | static                        | static                        | dynamic                       |
| Type inference            | `auto x = 5;`                 | `var x = 5;`                  | `var x = 5;` (Java 10+)       | implicit (no keyword)         |
| Explicit pointers          | ✅ `int* p`, `p->field`       | ❌ (only in `unsafe` blocks)  | ❌ none (references only)     | ❌ none (references only)     |
| Manual memory mgmt        | ✅ `new`/`delete`, RAII       | ❌ garbage collected           | ❌ garbage collected           | ❌ garbage collected           |
| Operator overloading       | ✅ fully supported             | ✅ supported (`operator +`)   | ❌ not supported                | ✅ via dunder methods (`__add__`) |
| Multiple inheritance       | ✅ classes                     | ❌ (interfaces only)           | ❌ (interfaces only)           | ✅ classes                     |
| Checked array bounds       | ❌ (`operator[]` unchecked, `.at()` checked) | ✅ throws `IndexOutOfRangeException` | ✅ throws `ArrayIndexOutOfBoundsException` | ✅ throws `IndexError` |

### 14.7 Null / Empty Handling

| Feature                  | C++                        | C#                           | Java                          | Python3                    |
|----------------------------|-------------------------------|---------------------------------|-----------------------------------|--------------------------------|
| Null value keyword        | `nullptr`                    | `null`                         | `null`                           | `None`                         |
| Null-coalescing operator  | ❌ none                       | ✅ `a ?? b`                     | ❌ none (use ternary)            | ❌ none (use `a if a is not None else b`, or `a or b`) |
| Null-conditional access   | ❌ none                       | ✅ `obj?.Field`                  | ❌ none (needs `Optional`)       | ❌ none (needs explicit check) |
| Optional/Maybe type       | `std::optional<T>` (C++17)   | `Nullable<T>` / nullable ref types | `Optional<T>`                 | implicit — any var can be `None` |

### 14.8 Iteration & Ranges

| Feature                  | C++                                | C#                                | Java                                | Python3                        |
|----------------------------|---------------------------------------|---------------------------------------|------------------------------------------|------------------------------------|
| Range-based for            | `for (auto& x : container)`          | `foreach (var x in collection)`      | `for (var x : collection)`              | `for x in iterable:`               |
| Numeric range loop         | `for (int i=0; i<n; i++)`            | `for (int i=0; i<n; i++)`            | `for (int i=0; i<n; i++)`               | `for i in range(n):`               |
| Step/stride range          | manual (`i += step`)                 | manual (`i += step`)                 | manual (`i += step`)                    | `range(start, stop, step)`         |
| List/array slicing         | ❌ none built-in (iterators/`substr`) | ❌ none built-in (`.Skip().Take()` LINQ) | ❌ none built-in (`Arrays.copyOfRange`) | ✅ `a[1:4]`, `a[::-1]`, `a[:-1]`   |
| List comprehension         | ❌ none                                | ✅ LINQ query/method syntax           | ❌ none (use Streams: `.stream().map()`) | ✅ `[x*2 for x in a if x>0]`       |
| Chained comparisons        | ❌ (`a < b < c` compiles but wrong!)  | ❌ not supported                      | ❌ not supported                          | ✅ `a < b < c` works as expected  |

> **Chained comparison trap:** `a < b < c` *compiles* in C++/C#/Java but does NOT mean what you think — it evaluates `(a < b) < c`, comparing a bool to `c`. Only Python evaluates it as `a < b and b < c`.

### 14.9 Switch / Pattern Matching

| Feature                     | C++                          | C#                                  | Java                                 | Python3                              |
|-------------------------------|---------------------------------|----------------------------------------|------------------------------------------|------------------------------------------|
| Switch statement             | ✅ `switch/case`, needs `break` | ✅ `switch/case`, needs `break`        | ✅ `switch/case`, needs `break`          | ❌ no `switch`; use `if/elif` or `match` |
| Pattern matching / match expr | ❌ none (C++ has no `match`)   | ✅ `switch` expressions + patterns (C# 8+) | ✅ `switch` expressions (Java 14+)      | ✅ `match/case` (Python 3.10+)           |
| Fallthrough by default        | ✅ yes (falls through unless `break`) | ❌ no (must use `goto case`)     | ✅ yes for classic `switch` (falls through unless `break`) | N/A (no switch)               |

### 14.10 Function/Variable Swap

| Language | Idiomatic swap                          |
|----------|-------------------------------------------|
| C++      | `swap(a, b);` (`<algorithm>`/`<utility>`) |
| C#       | `(a, b) = (b, a);` (tuple deconstruction, C# 7+) |
| Java     | ❌ no built-in — manual temp variable      |
| Python3  | ✅ `a, b = b, a`                           |

### 14.11 Exceptions

| Feature                   | C++                         | C#                           | Java                              | Python3                          |
|------------------------------|--------------------------------|---------------------------------|----------------------------------------|--------------------------------------|
| Try/catch keyword           | `try { } catch (Type e) { }`  | `try { } catch (Type e) { }`   | `try { } catch (Type e) { }`           | `try: ... except Type as e: ...`    |
| Finally block               | ❌ none (use RAII destructors) | ✅ `finally { }`                | ✅ `finally { }`                       | ✅ `finally:`                        |
| Checked exceptions          | ❌ none                        | ❌ none                         | ✅ (must declare `throws` or catch)    | ❌ none                              |
| Multi-catch                 | multiple `catch` blocks        | multiple `catch` blocks         | ✅ `catch (IOException \| SQLException e)` | ✅ `except (TypeError, ValueError):` |

---

## 15. Initialization & Iteration Patterns

### 15.1 Initializing a List/Array of single values

| Language | Syntax |
|----------|--------|
| C++      | `vector<int> a = {1, 2, 3};`  or  `int arr[] = {1, 2, 3};` |
| C#       | `List<int> a = new() { 1, 2, 3 };`  or  `int[] arr = { 1, 2, 3 };` |
| Java     | `List<Integer> a = new ArrayList<>(List.of(1, 2, 3));`  or  `int[] arr = {1, 2, 3};` |
| Python3  | `a = [1, 2, 3]` |

### 15.2 Initializing a List/Array of pairs (tuples)

| Language | Syntax |
|----------|--------|
| C++      | `vector<pair<int,int>> a = {{1,2}, {3,4}, {5,6}};` |
| C#       | `List<(int, int)> a = new() { (1,2), (3,4), (5,6) };` |
| Java     | No native tuple type. Use `int[]`: `List<int[]> a = new ArrayList<>(List.of(new int[]{1,2}, new int[]{3,4}));` — or a `record` (Java 16+): `record Pair(int first, int second) {}` then `List<Pair> a = new ArrayList<>(List.of(new Pair(1,2), new Pair(3,4)));` |
| Python3  | `a = [(1, 2), (3, 4), (5, 6)]` |

### 15.3 Initializing a Map/Dictionary (key → value)

| Language | Syntax |
|----------|--------|
| C++      | `unordered_map<string,int> m = {{"a",1}, {"b",2}};` |
| C#       | `Dictionary<string,int> m = new() { {"a",1}, {"b",2} };`  or  `new() { ["a"]=1, ["b"]=2 };` |
| Java     | `Map<String,Integer> m = new HashMap<>(Map.of("a",1, "b",2));` |
| Python3  | `m = {"a": 1, "b": 2}` |

### 15.4 Initializing a Set

| Language | Syntax |
|----------|--------|
| C++      | `unordered_set<int> s = {1, 2, 3};` |
| C#       | `HashSet<int> s = new() { 1, 2, 3 };` |
| Java     | `Set<Integer> s = new HashSet<>(Set.of(1, 2, 3));` |
| Python3  | `s = {1, 2, 3}` |

---

### 15.5 Iterating single values — index-based `for`

```cpp
// C++
for (int i = 0; i < a.size(); i++) {
    cout << a[i];
}
```
```csharp
// C#
for (int i = 0; i < a.Count; i++) {
    Console.WriteLine(a[i]);
}
```
```java
// Java
for (int i = 0; i < a.size(); i++) {
    System.out.println(a.get(i));
}
```
```python
# Python3
for i in range(len(a)):
    print(a[i])
```

### 15.6 Iterating single values — `foreach` / range-based `for`

```cpp
// C++ — use auto& to avoid copies
for (auto& x : a) cout << x;
```
```csharp
// C#
foreach (int x in a) Console.WriteLine(x);
```
```java
// Java
for (int x : a) System.out.println(x);
```
```python
# Python3
for x in a:
    print(x)
```

### 15.7 Iterating pairs/tuples with destructuring

```cpp
// C++17 structured bindings
for (auto& [x, y] : a) cout << x << "," << y;
```
```csharp
// C# tuple deconstruction
foreach (var (x, y) in a) Console.WriteLine($"{x},{y}");
```
```java
// Java — no destructuring; use array indices or record accessors
for (int[] p : a) System.out.println(p[0] + "," + p[1]);
// with a record:
for (Pair p : a) System.out.println(p.first() + "," + p.second());
```
```python
# Python3 — tuple unpacking
for x, y in a:
    print(x, y)
```

### 15.8 Iterating map/dictionary entries (key-value pairs)

```cpp
// C++17 structured bindings
for (auto& [k, v] : m) cout << k << "," << v;
```
```csharp
// C#
foreach (var kv in m) Console.WriteLine($"{kv.Key},{kv.Value}");
// or deconstruct directly (C# 7+)
foreach (var (k, v) in m) Console.WriteLine($"{k},{v}");
```
```java
// Java
for (Map.Entry<String, Integer> e : m.entrySet()) {
    System.out.println(e.getKey() + "," + e.getValue());
}
```
```python
# Python3
for k, v in m.items():
    print(k, v)
```

### 15.9 Iterating with index + value together (enumerate)

```cpp
// C++ — no built-in enumerate; track index manually
int i = 0;
for (auto& x : a) { cout << i << "," << x; i++; }
```
```csharp
// C# — LINQ Select with index
foreach (var (x, i) in a.Select((x, i) => (x, i)))
    Console.WriteLine($"{i},{x}");
```
```java
// Java — no built-in enumerate; use classic indexed loop
for (int i = 0; i < a.size(); i++) {
    System.out.println(i + "," + a.get(i));
}
```
```python
# Python3 — built-in enumerate()
for i, x in enumerate(a):
    print(i, x)
```

> **Key takeaways:**
> - Only **C++ (17+)** and **C#** support destructuring pairs/entries directly in a `for`/`foreach` (`auto& [k,v]` / `var (k,v)`). **Java has no destructuring** — you must call `.getKey()/.getValue()` or index into an array/record.
> - **Python's `enumerate()`** is the cleanest way to get index+value; the other three languages need a manual counter or (C#) LINQ's indexed `Select`.
> - **Java has no built-in tuple type** — the community typically uses `int[]`, `AbstractMap.SimpleEntry`, or a `record` for pairs.
> - Prefer `auto&` (C++) and reference-based iteration to avoid unnecessary copies when iterating large collections of structs/objects.

---

## Language-Specific Gotchas

- **C++**: `unordered_map`/`unordered_set` have no guaranteed order; `map`/`set` are ordered (red-black tree). Watch out for iterator invalidation after `erase`.
- **C#**: `Dictionary`/`HashSet` preserve insertion order in practice but it's **not guaranteed** by spec — don't rely on it. `PriorityQueue<TElement,TPriority>` only available .NET 6+.
- **Java**: `HashMap`/`HashSet` have no order guarantee; use `LinkedHashMap`/`LinkedHashSet` for insertion order, `TreeMap`/`TreeSet` for sorted order. Autoboxing (`Integer` vs `int`) can cause subtle bugs (`==` vs `.equals()`).
- **Python3**: `dict` preserves insertion order (guaranteed since 3.7). No built-in max-heap — negate values for `heapq`. Lists are dynamic arrays, not linked lists.
