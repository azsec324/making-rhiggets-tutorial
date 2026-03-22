# making-rhiggets-tutorial
Step by step tutorial on how to make Rhiggets. Offer documents for LLMs for doing it more efficiently.

## What is Rhiggets?
In short, **"Rhiggets"** is a special technique designed to solve a specific problem happening commonly in data storage. The term **"Mojibake"** covers all kinds of data-scrambling due to computers and programs having issues handling text encoding, though **Rhiggets** only solves one specific kind.

## What is Rhiggets best for?
As stated above, the **Rhiggets** technique is designed for one specific kind of **Mojibake**. Typically, when a string was saved as **UTF-8**, a standard **CJK character** takes up **3 bytes**. However, in another encoding system, **GBK**, an identical character takes only **2 bytes**. Therefore, if a string of 2 characters in *UTF-8* was mistakenly interpreted using *GBK*, the program would think there are 3 characters instead. If another mistake happens on top of that, the program would save the characters of what it **"thinks"** back, ending up with 3 characters in **UTF-8**.

For example, as a simple greeting in Chinese:
```
你好 -> E4 BD A0 | E5 A5 BD (In UTF-8)
```
However, the misbehaved program reads:
```
E4 BD | A0 E5 | A5 BD -> 浣犲ソ (In GBK)
```
Upon saving, the program saves the string back in UTF-8 again:
```
浣犲ソ -> E6 B5 A3 | E7 8A B2 | E3 82 BD (In UTF-8)
```
Which results in permanant alteration of the original data. Additionally, it is easy to notice that the size of the data has been increased by ***50%***, which is as well inefficient in storage and processing.

## How to perform Rhiggets?
#### ***UPDATE:** For LLM users, please check the SKILL.md, which was optimised for LLM performance.

The simple steps are as below:
1. Read the scrambled data in **UTF-8**, then find all the identical characters in **GBK** table.
2. Turn the data into bytes according to the GBK table. In this step, each character is supposed to be **2 bytes**.
3. Re-interpret the bytes in **UTF-8**. It should automatically read **3 byte chunks** instead of 2.

It is recommended using an text editor tool supporting multiple encoding systems if you want to do this manually. For example, CyberChef (Web) or Notepad++ (Local) or similiar tools are all capable of doing this job manually.

CyberChef: [Visit Here](https://gchq.github.io/CyberChef/)

Notepad++: [Visit Here](https://notepad-plus-plus.org/)
