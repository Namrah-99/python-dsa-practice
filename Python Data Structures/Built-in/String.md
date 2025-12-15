# String

<p align="center"><img width="798" height="423" alt="image" src="https://github.com/user-attachments/assets/d2b1b837-f23a-4a9e-8155-6f98a921f10d" />
</p>
<p align="center"><img width="785" height="325" alt="image" src="https://github.com/user-attachments/assets/f434f12a-d419-4296-96ab-c080ed1ba7a5" /></p>
<p align="center"><img width="802" height="265" alt="image" src="https://github.com/user-attachments/assets/55d6be5a-6f58-4f3f-9c25-9534596cbbe4" />
</p>
<p align="center"><img width="792" height="461" alt="image" src="https://github.com/user-attachments/assets/bf706958-e636-4b11-927a-8ae734414e3b" />
</p>
<p align="center"><img width="789" height="462" alt="image" src="https://github.com/user-attachments/assets/e298e608-f47f-40b4-b092-4a68dcf0049b" />
</p>
<p align="center"><img width="789" height="409" alt="image" src="https://github.com/user-attachments/assets/5008b4a6-1906-43f8-b139-2e120d77b88f" />
</p>
<p align="center"><img width="791" height="336" alt="image" src="https://github.com/user-attachments/assets/efced285-13ed-4689-a64b-70686bf30376" />
</p>
<p align="center"><img width="800" height="293" alt="image" src="https://github.com/user-attachments/assets/3a9ac520-e678-4d77-97b5-9adcb214e77e" />
</p>
<p align="center"><img width="782" height="527" alt="image" src="https://github.com/user-attachments/assets/b248ad7d-1178-41b3-ac27-96522b3cc8b5" />
</p>
<p align="center"><img width="790" height="380" alt="image" src="https://github.com/user-attachments/assets/666ff693-8927-4e9c-8da5-9c123d7010d1" />
</p>
<p align="center"><img width="796" height="397" alt="image" src="https://github.com/user-attachments/assets/25c5d819-b967-4d21-b0a7-e187df225489" />
</p>

**Strings are immutable, ordered sequences of characters, iterable, support concatenation and repetition, and can be used as dictionary or set keys.**

---

## Operations (with Complexity)

Strings in Python are immutable sequences of characters. Most operations create new strings.

<p align="center"><img width="789" height="407" alt="image" src="https://github.com/user-attachments/assets/4a5e2cf2-3256-4301-acab-495bda300cb1" />
</p>
<p align="center"><img width="793" height="502" alt="image" src="https://github.com/user-attachments/assets/76140c2e-8c43-4398-82eb-8d4a1c913f57" />
</p>
<p align="center"><img width="798" height="433" alt="image" src="https://github.com/user-attachments/assets/9cab8156-1008-4583-be22-a58613b15837" />
</p>
<p align="center"><img width="793" height="403" alt="image" src="https://github.com/user-attachments/assets/653ff759-abf6-4417-9d60-f566716aec70" />
</p>
<p align="center"><img width="790" height="418" alt="image" src="https://github.com/user-attachments/assets/34c0c623-e1f6-4e12-ae76-a93df2b3ca10" />
</p>
<p align="center"><img width="787" height="417" alt="image" src="https://github.com/user-attachments/assets/6429092f-6f4c-4adb-bc26-1a10f138850f" />
</p>
<p align="center"><img width="789" height="373" alt="image" src="https://github.com/user-attachments/assets/b0e8a48f-703c-46a9-977d-e704fc53bf5a" />
</p>
<p align="center"><img width="793" height="391" alt="image" src="https://github.com/user-attachments/assets/f2268987-7f7e-445b-9738-14b15f756dd6" />
</p>
<p align="center"><img width="799" height="392" alt="image" src="https://github.com/user-attachments/assets/eed692e1-ae5d-4313-aa22-3144c9e805c7" />
</p>
<p align="center"><img width="789" height="370" alt="image" src="https://github.com/user-attachments/assets/79162e28-b257-4711-add7-8e4385a1e4e9" />
</p>
<p align="center"><img width="792" height="341" alt="image" src="https://github.com/user-attachments/assets/f82fa76b-eab1-4f30-a384-9e5852ae8828" />
</p>
<p align="center"><img width="792" height="372" alt="image" src="https://github.com/user-attachments/assets/9c4dc449-a2e2-4d98-990d-dba71b697c1b" />
</p>
<p align="center"><img width="789" height="377" alt="image" src="https://github.com/user-attachments/assets/df81d808-ac17-43ad-a81c-69d377398294" />
</p>
<p align="center"><img width="795" height="483" alt="image" src="https://github.com/user-attachments/assets/387455cc-61df-4fae-90f3-c3b4df581c23" />
</p>

## Takeaways

- ✔ Strings are immutable sequences, so all modifications produce new strings.
- ✔ Indexing, slicing, and iteration are supported.
- ✔ Fast lookup as dictionary/set key because strings are hashable.
- ✔ Be mindful of time/space when concatenating large strings repeatedly (use join in that case).

---

## ✅ When to Use str

<p align="center"><img width="802" height="610" alt="image" src="https://github.com/user-attachments/assets/e5d7b751-3d96-493e-9ef6-68d2a009afee" />
</p>

## ❌ When NOT to Use str

<p align="center"><img width="798" height="657" alt="image" src="https://github.com/user-attachments/assets/7ecd84d1-cec7-45b4-a460-147513845936" />
</p>

**Use strings for read-only textual data and identifiers. Avoid them when frequent mutation, large incremental building, or non-text data is required.**

## Common Pitfalls

- Strings are immutable → cannot do s[0] = 'a'

- Concatenation in loops is O(n²) → use ''.join(list_of_strings)

- Index out of range → always check length

- Strings are sequences of characters → indexing returns a string, not a char type

## Tips for Interviews

- Use slicing for reversal → s[::-1]

- Use Counter for frequency-based problems

- Use two pointers for palindrome/subarray

- Use sliding window + dictionary for substring problems

- Avoid concatenation in loops → build list + ''.join()

- Strings are immutable → think about space usage

**Strings are sequences of characters. Think in terms of two pointers, sliding window, frequency counting, hashing, and stacks. Immutability means operations often create new strings, so avoid excessive concatenation in loops.**
