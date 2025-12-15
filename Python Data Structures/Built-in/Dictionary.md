# Dictionary

<p align="center"><img width="717" height="356" alt="image" src="https://github.com/user-attachments/assets/2235f4db-e2fc-462b-a31d-ea0fdb622ec0" />
</p>

<p align="center"><img width="721" height="294" alt="image" src="https://github.com/user-attachments/assets/ef604b4b-b55d-491f-b1e6-fbe85a42137e" />
</p>
<p align="center"><img width="717" height="429" alt="image" src="https://github.com/user-attachments/assets/c582fd7d-2a5e-493e-a9cd-e26f894bcb74" />
</p>
<p align="center"><img width="670" height="669" alt="image" src="https://github.com/user-attachments/assets/7661cb2e-0c78-4d11-8d52-1b47492b13e6" />
</p>
<p align="center"><img width="718" height="573" alt="image" src="https://github.com/user-attachments/assets/ac13322a-9604-4db8-beb7-445e5b96ef73" />
</p>
<p align="center"><img width="718" height="641" alt="image" src="https://github.com/user-attachments/assets/754ff4d9-606d-4b55-a6c6-c8e297d048e6" />
</p>
<p align="center"><img width="736" height="674" alt="image" src="https://github.com/user-attachments/assets/e8a6a708-f1ed-4867-b446-e478b2122cfb" />
</p>

**Use dictionaries when you need fast key-based access, mapping of unique keys to values, and mutable collections.**

---

## Operations (with Complexity)

📌 Important: Dictionaries are hash table-based, so most key-based operations are O(1) average case.

<p align="center"><img width="643" height="774" alt="image" src="https://github.com/user-attachments/assets/c0bda8ad-f8e3-4cc3-a938-34c338755ad1" />
</p>

### Time & Space Complexity
<p align="center"><img width="716" height="303" alt="image" src="https://github.com/user-attachments/assets/31ab5c33-37a3-48bc-b2cd-eac0e73bc7aa" />
</p>

<p align="center"><img width="733" height="747" alt="image" src="https://github.com/user-attachments/assets/2a84d2c6-ab98-44a4-98a4-7149ba2d1cce" />
</p>
<p align="center"><img width="712" height="729" alt="image" src="https://github.com/user-attachments/assets/e5cd5061-96cf-4d73-96d8-aca234ffd6ad" />
</p>
<p align="center"><img width="711" height="705" alt="image" src="https://github.com/user-attachments/assets/6b094ad7-6b89-4ca5-9c16-03d1faa3d2a6" />
</p>
<p align="center"><img width="716" height="365" alt="image" src="https://github.com/user-attachments/assets/827bbe96-ce2f-44b4-bafb-e18838a7cb17" />
</p>
<p align="center"><img width="714" height="507" alt="image" src="https://github.com/user-attachments/assets/7aafdc24-190d-4f2c-926d-ff2a19ab9264" />
</p>
<p align="center"><img width="718" height="706" alt="image" src="https://github.com/user-attachments/assets/531e4283-b029-4caf-9929-a0537f9460bc" />
</p>
<p align="center"><img width="714" height="610" alt="image" src="https://github.com/user-attachments/assets/4d5b7beb-4b34-4ad4-9253-98cb48b6baaa" />
</p>

<p align="center"><img width="715" height="285" alt="image" src="https://github.com/user-attachments/assets/9386ebbb-b6b8-42e9-a191-4f13cf5e5d03" />
</p>

## Key Takeaways

- ✔ Dictionaries are best for key-based fast access
- ✔ Mutable: add, update, remove easily
- ✔ Use .get() for safe access
- ✔ Avoid using unhashable types as keys

## Why Dictionaries Are Important in DSA & LeetCode

Dictionaries are extremely powerful for:

- Fast lookups → `O(1)` average

- Counting / frequency problems

- Memoization / caching

- Mapping relationships → graphs, indices

- Hash maps for complement lookups → e.g., Two Sum

Almost every LeetCode problem involving counts, maps, or unique tracking benefits from dictionaries.

## Dictionary Techniques to Remember
- Frequency Map / Count Map → Most used

- Complement Map → Two Sum, K-sum variants

- Index Map → Track positions efficiently

- Memoization / Caching → DP

- Grouping / Bucketing → Strings, tuples, categories

- Sliding Window / Window Map → Variable-length subarray/string problems

## Common Pitfalls

- Forgetting .get() → KeyError

- Using mutable types as keys → TypeError

- Overwriting keys accidentally

- Assuming dictionary order in older Python (<3.7)

---

## ✅ When to Use dict

<p align="center"><img width="725" height="471" alt="image" src="https://github.com/user-attachments/assets/acfb3ada-e3f8-46ae-9b10-7fdb43ccc7b8" />
</p>

## ❌ When NOT to Use dict

<p align="center"><img width="729" height="565" alt="image" src="https://github.com/user-attachments/assets/454ae2c5-30f7-4948-a5b7-ba742790136d" />
</p>

**Use dictionaries for key-based access, mapping, and mutable structured data. Avoid them when only order, duplicates, or positional indexing is needed.**

## Tips & Best Practices

- Use `.get()` or `defaultdict(int/list)` to avoid KeyError

- Use tuples as keys for multi-variable states

- Dictionary + Heap → Top K problems

- Avoid modifying dict while iterating → iterate over `.items()` or copy

- Check membership → `if key in d` instead of `try/except`

They are often the difference between an O(n²) brute-force solution and an O(n) optimized solution.
