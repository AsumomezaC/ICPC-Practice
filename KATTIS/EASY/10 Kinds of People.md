---
tags:
  - ICPC
  - Programación
  - Software
---
# 10 Kinds of People
The world is made up of  kinds of people, those who understand binary and those who do not. These different kinds of people do not always get along so well. Bob might ask for a  ounce coffee (meaning binary) and Alice might make misinterpret his request as being in decimal and give him a  ounce coffee (binary). After Sue explains that this much coffee costs  dollars (decimal), Bob might assume he only has to pay  dollars (interpreting the price as being in binary). In response to these differences that are difficult to resolve, these two groups have divided the world into two regions, the binary-friendly zones and the decimal-friendly zones. They have even published a map like the following to help people keep up with where the areas are (they have used ones and zeros so nobody would have trouble reading it).

1111100000  
1111000000  
1110000011  
0111100111  
0011111111

Users of binary have to stay in the zones marked with a zero. Users of decimal have to stay in the zones marked with a one. You have to figure out if it is possible for either type of person to get between various locations of interest. People can move north, south, east or west, but cannot move diagonally.

## Input

Input starts with a line containing two positive integers,  and . The next  input lines give the contents of the map, each line containing exactly  characters (which are all chosen from  or ).

The next line has an integer . The following  lines each contain one query, given as four integers:  and . These two pairs indicate two locations on the map, and their limits are  and .

## Output

For each query, output binary if a binary user can start from location  and move to location . Output decimal if a decimal user can move between the two locations. Otherwise, output neither.

|Sample Input 1|Sample Output 1|
|---|---|
|1 4<br>1100<br>2<br>1 1 1 4<br>1 1 1 1|neither<br>decimal|

|Sample Input 2|Sample Output 2|
|---|---|
|10 20<br>11111111111111111111<br>11000000000000000101<br>11111111111111110000<br>11111111111111110000<br>11000000000000000111<br>00011111111111111111<br>00111111111111111111<br>10000000000000001111<br>11111111111111111111<br>11111111111111111111<br>3<br>2 3 8 16<br>8 1 7 3<br>1 1 10 20|binary<br>decimal<br>neither|
## Código
### [[Python]]
```python

```
### [[C]] o [[C++]]
```c

```
## Explicación

## Temas relacionados
- 
## Link
[10 Kinds of People – Kattis, Kattis](https://open.kattis.com/problems/10kindsofpeople)