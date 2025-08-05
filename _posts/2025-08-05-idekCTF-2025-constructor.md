---
title: 'idekCTF 2025 constructor'
date: 2025-08-05
permalink: /posts/2025/08/idekCTF-2025-constructor/
tags:
  - CTF solution
---


The category of the challenge is rev. At first, I tried to execute the binary and here's the output.
![](images/idekCTF2025/initial_output.png)

As you can see that, it only showed the emoji. But, what about passing the arguments to it?
![](images/idekCTF2025/first_try.png)

It said wrong!. To figure out what's going on here, I opend up the IDA to reverse it.
To effeciently track the binary, I started to look at the address of "Wrong!". It appeared at the 0x40301C.
To trace back the function that use "Wrong!" string, and I found it at the address of 0x40111E.
This function function might be the main function since it used the "Wrong!". Let's move on to the first part of this function.
I found that there's a for loop here. To understand what it is, I opend up the gdb to understand it.
Let's set the breakpoint at the address of 0x4010AF to understand the registers info. After serveral run, we found the format of flag!
![](images/idekCTF2025/flag_format.png)

Time to leak out the flag!
![](images/idekCTF2025/flag.png)

```bash
flag: idek{he4rd_0f_constructors?_now_you_d1d!!}
```
