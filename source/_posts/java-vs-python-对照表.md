---
title: java vs python对照表
date: 2025-11-23 10:54:51
tags: code
---

最核心的区别在于：**Python 是“拿来就用”，Java 是“先声明再用”且“类型严格”。**

### 1. 最让人头大的：获取长度/大小

这是 Java 新手最容易混淆的地方，务必死记硬背。

| **对象类型**                   | **Python (len走天下)** | **Java (乱七八糟的各种写法)** | **记忆口诀**                               |
| ------------------------------ | ---------------------- | ----------------------------- | ------------------------------------------ |
| **数组** (`int[]`)             | `len(arr)`             | `arr.length`                  | 数组是对象，`length` 是**属性** (无括号)   |
| **字符串** (`String`)          | `len(s)`               | `s.length()`                  | 字符串是类，`length()` 是**方法** (有括号) |
| **集合/列表** (`List/Set/Map`) | `len(list)`            | `list.size()`                 | 集合容器统一用 `size()`                    |

### 2. 数组与列表 (Array & ArrayList)

在 LeetCode 中，定长数组用 `int[]`，变长列表用 `ArrayList`（类似 Python 的 `list`）。

| **操作**      | **Python (list)** | **Java (ArrayList<Integer>)**             | **Java (int[] 数组)**           |
| ------------- | ----------------- | ----------------------------------------- | ------------------------------- |
| **初始化**    | `nums = []`       | `List<Integer> list = new ArrayList<>();` | `int[] arr = new int[10];`      |
| **添加元素**  | `nums.append(x)`  | `list.add(x)`                             | (不可扩容，只能赋值 `arr[i]=x`) |
| **访问元素**  | `nums[i]`         | `list.get(i)`                             | `arr[i]`                        |
| **修改元素**  | `nums[i] = x`     | `list.set(i, x)`                          | `arr[i] = x`                    |
| **排序**      | `nums.sort()`     | `Collections.sort(list)`                  | `Arrays.sort(arr)`              |
| **切片/截取** | `nums[i:j]`       | `list.subList(i, j)`                      | `Arrays.copyOfRange(arr, i, j)` |

**⚠️ Java 坑点：** `ArrayList` 里面只能存对象 (`Integer`)，不能存基本类型 (`int`)。但在 `int[]` 数组里存的是 `int`。

### 3. 字符串 (String)

Java 的 String 是**不可变**的，修改字符串必须通过 `StringBuilder`。

| **操作**     | **Python (str)** | **Java (String)**                           |
| ------------ | ---------------- | ------------------------------------------- |
| **访问字符** | `s[i]`           | `s.charAt(i)` (**不能用** `[]`)             |
| **判等**     | `s1 == s2`       | `s1.equals(s2)` (**千万别用** `==`)         |
| **拼接**     | `s1 + s2`        | `s1 + s2` (慢) 或 `sb.append(s2)` (快)      |
| **转为数组** | `list(s)`        | `s.toCharArray()`                           |
| **子串**     | `s[i:j]`         | `s.substring(i, j)`                         |
| **包含**     | `'a' in s`       | `s.contains("a")` 或 `s.indexOf('a') != -1` |

### 4. 哈希表 (HashMap / HashSet)

刷题神器，Java 写法非常繁琐，但逻辑严密。

| **操作**         | **Python (dict / set)**  | **Java (HashMap / HashSet)**           |
| ---------------- | ------------------------ | -------------------------------------- |
| **初始化**       | `d = {}`                 | `Map<K, V> map = new HashMap<>();`     |
| **存值**         | `d[key] = val`           | `map.put(key, val);`                   |
| **取值**         | `d[key]`                 | `map.get(key);`                        |
| **取值(带默认)** | `d.get(key, 0)`          | `map.getOrDefault(key, 0);` (**高频**) |
| **判断Key存在**  | `key in d`               | `map.containsKey(key);`                |
| **遍历**         | `for k, v in d.items():` | `for (Key k : map.keySet())` (推荐)    |

### 5. 栈、队列与堆 (Stack, Queue, Heap)

Java 中通常用 `Deque` 接口双修栈和队列。

| **场景**         | **Python**              | **Java 实现类**                                      | **Java 核心 API**                  |
| ---------------- | ----------------------- | ---------------------------------------------------- | ---------------------------------- |
| **队列 (Queue)** | `collections.deque`     | `Deque<Integer> q = new ArrayDeque<>();`             | `q.offer(x)` (进), `q.poll()` (出) |
| **栈 (Stack)**   | `list` (`append`/`pop`) | `Deque<Integer> s = new ArrayDeque<>();`             | `s.push(x)` (进), `s.pop()` (出)   |
| **小顶堆**       | `heapq.heappush`        | `PriorityQueue<Integer> pq = new PriorityQueue<>();` | `pq.offer(x)`, `pq.poll()`         |
| **大顶堆**       | `heapq` (存负数 trick)  | `new PriorityQueue<>((a, b) -> b - a);`              | 利用 Lambda 表达式自定义比较器     |

### 6. 循环与逻辑控制 (Loops)

Java 的循环更原始，但也更灵活。

- **Python:**

  Python

  ```java
  for x in nums:
      print(x)
  ```

- **Java (增强 For 循环 - 推荐):**

  Java

  ```java
  for (int x : nums) {
      System.out.println(x);
  }
  ```

- **Java (普通 For 循环 - 需要索引时):**

  Java

  ```java
  for (int i = 0; i < nums.length; i++) {
      // i 是索引
  }
  ```

