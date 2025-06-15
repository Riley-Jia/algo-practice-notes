## V getOrDefault(Object key, V defaultValue)

- **Purpose**: Returns the value for a given key if present; otherwise returns the provided default.
- **功能**：当 key 存在时返回对应 value；否则返回你指定的默认值。
- **Typical Usage**: Avoids null checks; common in frequency counting.
- **应用场景**：常用于计数、频率统计等，避免 `null` 判断。

## Basic Example
```bash
# common usage
Map<Character, Integer> map = new HashMap<>();
map.put("apple", 3);

int appleValue = map.getOrDefault("apple",0);
int bananaValue = map.getOrDefault("banana", 0);

System.out.println(appleValue); // 3
System.out.println(bananaValue); // 0

# typically used for counting
String s = "abacd";
Map<Character,Integer> freq = new HashMap<>();

for(char c : s)
{
    freq.put(c, map.getOrDefault(c, 0) + 1);
}

System.out.println(freq); // {a=2, b=1, c=1, d=1}
```

---

_Last updated: June 15, 2025_  
_Compiled by: Riley_
