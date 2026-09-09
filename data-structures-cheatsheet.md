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

## Language-Specific Gotchas

- **C++**: `unordered_map`/`unordered_set` have no guaranteed order; `map`/`set` are ordered (red-black tree). Watch out for iterator invalidation after `erase`.
- **C#**: `Dictionary`/`HashSet` preserve insertion order in practice but it's **not guaranteed** by spec — don't rely on it. `PriorityQueue<TElement,TPriority>` only available .NET 6+.
- **Java**: `HashMap`/`HashSet` have no order guarantee; use `LinkedHashMap`/`LinkedHashSet` for insertion order, `TreeMap`/`TreeSet` for sorted order. Autoboxing (`Integer` vs `int`) can cause subtle bugs (`==` vs `.equals()`).
- **Python3**: `dict` preserves insertion order (guaranteed since 3.7). No built-in max-heap — negate values for `heapq`. Lists are dynamic arrays, not linked lists.
