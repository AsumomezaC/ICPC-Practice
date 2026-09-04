#ICPC #Programación #Software 
# lv-able
A string is “lv”-able if it contains the contiguous substring “lv”.

You are given a string  with  characters, and you want to make it “lv”-able in as few operations as possible.

You are allowed to do any of these operations:

- Remove any character at any position.
    
- Insert any character at any position.
    
- Replace any character by any other character at any position.
    
- Choose any consecutive interval of characters, and reverse the order of the characters in it.
    

Now make the string “lv”-able!

## Input

The first line of input contains an integer  (), the number of characters in the initial string.

The second line contains the string , which consists of  lowercase letters a-z.

## Output

Print an integer: the minimum number of operations such that the string  becomes “lv”-able.

## Scoring

Your solution will be tested on a set of test groups, each worth a number of points. Each test group contains a set of test cases. To get the points for a test group you need to solve all test cases in the test group.

|   |   |   |
|---|---|---|
|**Group**|**Points**|**Constraints**|
||||
|||No additional constraints.|

## Explanation of Samples

In sample , you can reverse the substring “ov”, resulting in lvoable, which then contains “lv”.

In sample , we can replace the “e” with a “v”, which then contains “lv”.

In sample , the string already contains “lv”.

|Sample Input 1|Sample Output 1|
|---|---|
|7<br>lovable|1|

|Sample Input 2|Sample Output 2|
|---|---|
|6<br>google|1|

|Sample Input 3|Sample Output 3|
|---|---|
|6<br>lvable|0|
## Código
### [[Python]]
```python
n = int(input())

word = input()

res = 2

for c in range(n):
    if word[c] == 'l':
        res = 1
    if word[c] == 'v':
        res = 1
        if word[c-1] == 'l':
            res = 0
            break
print(res)
```

o se puede usar simplemente "in":
```python
n = int(input()) # este no es necesario de guardar
word = input()

if "lv" in word:
    print(0)
elif "l" in word or "v" in word:
    print(1)
else:
    print(2)
```
### [[C]] o [[C++]]
```c
#include <bits/stdc++.h> // agrega todo lo que existe en C y C++ -más trabajo para el compilador pero corre igual de rápido una vez compilado-
using namespace std;

int main(void) {
    string texto;
    int n, res = 2;
    scanf("%d", &n);
    cin >> texto;
    for(int i=0; i<n;i++){
        if(texto[i] == 'l'){
            res = 1;
        }
        if(texto[i] == 'v'){
            res = 1;
            if(i-1 >=0){ // mejoramos el código impidiendo que se tome basura
                if(texto[i-1] == 'l'){
                    res = 0;
                    break;
                }
            }
        }
    }
    printf("%d\n", res);

    return 0;
}
```
## Explicación
Para saber cuantos pasos hay que hacer para hacer una palabra 'lv-able', debemos determinar en cual de los 3 casos nos encontramos:
- **Peor de los casos**: no se contiene ni 'l' ni 'v' en el string, por lo cual para crearlo, se ocupan ==2 movimientos==.
- **Mejor de los casos**: 'lv' ya se encuentra en el string, por lo cual se ocupan ==0 movimientos==.
- **Tercer caso**: se encuentra 'l' y/o 'v' pero no se encuentra la forma 'lv'; por lo cual se ocupa ==1 movimiento==.
## Temas relacionados
- [[Secuencias - Python]]
## Link
["lv"-able – Kattis, Kattis](https://open.kattis.com/problems/lvable)