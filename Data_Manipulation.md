# Data Manipulation

## Translating Characters

### Solve

**Flag:** `pwn.college{kkD9tuj328vpRcXk28CJ2kgWs49.01MxEzNxwSO5EzNzEzW}`

I ran the `/challenge/run` first and then
Then i ran the cmd again but piped it to tr with capital alphabets followed with small as 1st argument and small followed by caps as 2nd argument, thus swapping the case.

```
hacker@data~translating-characters:~$ /challenge/run
Your case-swapped flag:
PWN.COLLEGE{KKd9TUJ328VPrCxK28cj2KGwS49.01mXeZnXWso5eZnZeZw}
hacker@data~translating-characters:~$ /challenge/run | tr ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHI
JKLMNOPQRSTUVWXYZ
yOUR CASE-SWAPPED FLAG:
pwn.college{kkD9tuj328vpRcXk28CJ2kgWs49.01MxEzNxwSO5EzNzEzW}

hacker@data~translating-characters:~$ 
```

### New Learnings
The `tr` command swaps character cases using two arguments, can be used to swap chars and other applications.

---

## Deleting Characters

### Solve

**Flag:** `pwn.college{QV5bQ8FWeCcKWb_FtxSBmJ6CFRP.0FNxEzNxwSO5EzNzEzW}`

To solve this, i first ran `/challenge/run`, saw it was filled with decoys of "^%" so I piped it with `tr -d ^%` and got the flag


```
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
p^%w^n%.%c^%o^l^le^g^%e^{^%QV%5b^%Q^%8%F^%W^%e^%C^c^K%W^%b^%_^F^txS%B^m^J^6^C%FR^%P%.0^%F^%Nx^E%z%N%x%w^SO5^%Ez^N%z%E%z^W^%}%^
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{QV5bQ8FWeCcKWb_FtxSBmJ6CFRP.0FNxEzNxwSO5EzNzEzW}
hacker@data~deleting-characters:~$ 
```

### New Learnings
`tr -d` deletes specified characters from input streams

---

## Deleting Newlines

### Solve

**Flag:** `pwn.college{oPFvKLOnNRDH2C_33zH4dag6VY-.0VNxEzNxwSO5EzNzEzW}`

```
hacker@data~deleting-newlines:~$ /challenge/run
Your line-split flag: 
p
w
n.
c
o
l
l
e
g
e{
o
P
Fv
K
L
OnNRD
H
2C_
33zH
4d
a
g6
V
Y
-
.
0
V
Nx
E
z
Nx
wS
O
5
Ez
NzE
z
W}

hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{oPFvKLOnNRDH2C_33zH4dag6VY-.0VNxEzNxwSO5EzNzEzW}hacker@data~deleting-newlines:~$ 
```

### New Learnings
`tr -d "\n"` removes newline characters to join multi-line output into a single line.

---

## Extracting the First Lines with Head

### Solve

**Flag:** `pwn.college{ofuBA_WBKDFi07FMqV-NQyA2upE.0lNxEzNxwSO5EzNzEzW}`

In this challenge, we were asked to pipe the first 7 lines of `/challenge/pwn` to `/challenge/college`, which i achieved by running `/challenge/pwn | head -n 7 | /challenge/college`, and got the flag.

```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{ofuBA_WBKDFi07FMqV-NQyA2upE.0lNxEzNxwSO5EzNzEzW}
hacker@data~extracting-the-first-lines-with-head:~$ 

```

### New Learnings

`head -n N` extracts the first N lines from input, commonly used in pipeline operations.

---

## Extracting Specific Sections of Text

### Solve

**Flag:** `pwn.college{YhWc4E-D6n-OFW7gdPOHUZD1_cy.01NxEzNxwSO5EzNzEzW}`

I ran `/challenge/run` and found out that the flag chars are present in the 2nd column and are separated by newlines, so i ran `/challenge/run | cut -d " " -f 2 | tr -d "\n"`, to get the flag.


```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
2794 p
11081 w
29662 n
10666 .
24970 c
23017 o
25358 l
23723 l
31220 e
13229 g
25186 e
19758 {
11754 Y
1117 h
2192 W
13962 c
20290 4
7368 E
15276 -
7336 D
29231 6
31682 n
11282 -
24258 O
8131 F
24266 W
17928 7
30193 g
17308 d
19801 P
14439 O
311 H
28185 U
22381 Z
21584 D
24641 1
26733 _
2867 c
24792 y
13419 .
619 0
19887 1
22641 N
6220 x
12264 E
11911 z
24579 N
28420 x
8654 w
29889 S
11547 O
25623 5
9798 E
27927 z
2678 N
1344 z
22041 E
12302 z
1712 W
14515 }
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{YhWc4E-D6n-OFW7gdPOHUZD1_cy.01NxEzNxwSO5EzNzEzW}hacker@data~extracting-specific-sections-of-text:~$ 
```

### New Learnings
``cut -d " " -f N`` extracts specific columns using specified delmiter after -d (space delimiter in my case), and -f N selects the Nth column (2nd in my case).

---

## Sorting Data

### Solve

**Flag:** `pwn.college{cwG6ypuBMnDxCtS4PrBzLtZ9z7U.0FM0MDOxwSO5EzNzEzW}`

Used `-r` with sort to sort in reverse, as flag was mentioned to be the last when sorted by alphabetical order.

```
hacker@data~sorting-data:~$ sort /challenge/flags.txt -r | less
pwn.college{cwG6ypuBMnDxCtS4PrBzLtZ9z7U.0FM0MDOxwSO5EzNzEzW}
pwn.college{cwG6ypuBMnDxCtS4PrBzLtZ9z7U.0FM0MDOxwSO5EzNzEzW}
pwn.college{cwG6ypuBMnDxCtS4PrBzLtZ9z7U.0FM0MDOxwSO5EzNzEzW}
pwn.college{cwG6ypuBMnDxCtS4PrBzLtZ9z7U.0FM0MDOxwSN5EzNzEzW}
pwn.college{cwG6ypuBMnDxCtS4PrBzLtZ9z7U.0FL0MDOxwSO5EzNzEzW}
...
```

### New Learnings
`sort` can be used for various sorting application :
-r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order!
# END
