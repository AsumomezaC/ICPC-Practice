#ICPC #Programación #Software 
# Blandad Best
Níels is at his favourite kebab place, KFFÍ (Kebab Fyrir Forritara á Íslandi) and now he needs to decide what type of meat he wants on his kebab. KFFÍ offers a wide range of options, a whole two different types, beef or chicken. If you are like Níels, you always prefer getting both mixed together. Níels goes to the counter and asks for special offer number 5, as always, and asks what type of meat they are offering today. Of course, if they offer beef and chicken then he will get them mixed together, otherwise he is content with only taking the one they have, special offer 5 is so good anyway.

Curious as to what Níels got on his kebab, you go to the server and ask him what type of meat they are offering today.
## Input

The first line of input contains a positive integer , the number of meat types KFFÍ is offering today. Next  lines will follow, each one with a unique meat type. The meat type is either "nautakjot" or "kjuklingur".
## Output

Output what type of meat Níels got with his offer. If Níels had only "nautakjot" then you should write "nautakjot", if he only got "kjuklingur" then you should write "kjuklingur" and if Níels had both then you should write "blandad best".
## Scoring

|   |   |   |
|---|---|---|
|Group|Points|Constraints|
|1|100||

|Sample Input 1|Sample Output 1|
|---|---|
|1<br>kjuklingur|kjuklingur|

|Sample Input 2|Sample Output 2|
|---|---|
|1<br>nautakjot|nautakjot|

|Sample Input 3|Sample Output 3|
|---|---|
|2<br>nautakjot<br>kjuklingur|blandad best|

|Sample Input 4|Sample Output 4|
|---|---|
|2<br>kjuklingur<br>nautakjot|blandad best|
## Código
### [[Python]]
```python
types = int(input())

if (types == 2):
    print("blandad best")
else:
    print(input())
```
### [[C]] o [[C++]]
```c
#include <stdio.h>

int main(void) {
    int type;
    scanf("%d", &type);
    if(type == 2){
        puts("blandad best");
    } else {
        char carne[20];
        scanf("%s",carne);
        puts(carne);
    }
    return 0;
}
```
## Explicación
Primero checamos la primera línea; si estás los dos tipos de carne es el caso del festejo, de lo contrario, seleccionamos el único tipo de carne que hay
## Temas relacionados
- [[Control de flujo]]
## Link
[Blandað Best – Kattis, Kattis](https://open.kattis.com/problems/blandadbest)