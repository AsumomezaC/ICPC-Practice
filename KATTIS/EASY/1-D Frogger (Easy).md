---
tags:
  - ICPC
  - Programación
  - Software
---
# 1-D Frogger (Easy)
_Frogger_ is a classic -D video game that challenges the player to move a frog character safely across a traffic-filled road and a hazardous river. What is not well known is that Frogger actually began as a prototype board game based on a -D concept at a now-defunct toy company.[1](https://open.kattis.com/problems/1dfroggereasy#a0000000005) After spending millions of dollars following the advice of consultants, company executives realized that the resulting game was almost completely deterministic, and therefore not much fun to play,[2](https://open.kattis.com/problems/1dfroggereasy#a0000000006) so they sold all Frogger rights to a video game company in an attempt to recoup some of the development costs. The rest, as they say, is video game history.

The original -D Frogger design, however, makes for good programming competition problems. Here is how the game works. The board is a row of  squares, each of which contains a non-zero integer. These squares are indexed , from left to right. To start the game, the player rolls an -sided die with one of the distinct indices on each side, and places a frog token on the board square with the resulting index. The player then randomly selects a card from a deck of cards with integers written on them (one per card); the integer on each card is contained in at least one board square. The number on the selected card is the _magic number_ (or _goal number_) for this instance of the game.

The player then applies the following rule as many times as necessary until the game ends:

- If the frog is on a square containing a positive integer, , the frog makes a length- hop to the right. (Hop distance is measured in board square units.)
    
- If the frog is on a square containing a negative integer, , the frog makes a length- hop to the left (note the absolute value).
    

The game ends as soon as the frog encounters one of the following four fates:

1. The frog lands on a square containing the magic number. This is the only winning outcome for the player. Note that if the frog starts on a square containing the magic number, the player wins immediately (i.e., after  hops).
    
2. The frog falls off the left end of the board.
    
3. The frog falls off the right end of the board.
    
4. The frog hops onto a square where the frog has been before, and therefore is trapped in a cycle.
    

Let  be the number of hops the frog makes before the game ends. Given an instance of the game, your task is to determine the frog’s fate and the corresponding value of .

## Input

The first line of input contains three space-separated integers, , , , where  is the number of board squares ,  is the index of the frog’s starting square , and  is the magic number. This is followed by a line containing  space-separated non-zero integers. These are the numbers in the board squares in order from left to right. Each board square number is in the interval , and the magic number is guaranteed to be one of the board square numbers.

## Output

Output two lines. The first line contains a word indicating the fate of the frog, one of ‘magic’, ‘left’, ‘right’, ‘cycle’, corresponding to the four fates listed above, respectively. The second line contains the integer , the number of hops the frog makes before encountering its fate.

|Sample Input 1|Sample Output 1|
|---|---|
|6 4 42<br>-9 1 42 -2 -3 -3|magic<br>2|

|Sample Input 2|Sample Output 2|
|---|---|
|8 2 13<br>7 5 4 2 13 -2 -3 6|cycle<br>4|

**Footnotes**

1. This story might be apocryphal.
2. That’s not to say that deterministic games are never fun; some are, and are quite popular.
## Código
### [[Python]]
```python
n,s,m = map(int, input().split())

a = list(map(int, input().split()))
a.insert(0,0) # se inserta un elemento 0 para que los valores empiezen en 1

visit = [False] * len(a)

count = 0

while True:
    if s>n:
        print("right")
        break
    if s<1:
        print("left")
        break
    if a[s] == m:
        print("magic")
        break
    if visit[s]:
        print("cycle")
        break
    else:
        visit[s]=True
        s+=a[s]
        count+=1
        
print(count)
```
### [[C]] o [[C++]]
```c
#include <bits/stdc++.h> // agrega todo lo que existe en C y C++ -más trabajo para el compilador pero corre igual de rápido una vez compilado-
using namespace std; // ahorra el uso de std en funciones estandar

int main(void) {
    // Tu código aquí
    int n, s, m;
    
    scanf("%d %d %d", &n, &s, &m);
    int pos[n+1], visit[n+1];
    for(int i=1; i<=n; i++){
        cin >> pos[i];
        visit[i]=0;
    }
    
    int count=0;
    
    while(true){
        if(s>n){
            puts("right");
            break;
        }
        if (s<1){
            puts("left");
            break;
        }
        if (pos[s] == m){
            puts("magic");
            break;
        }
        if (visit[s]){
            puts("cycle");
            break;
        }
        visit[s]=1;
        s+=pos[s];
        count++;
    }
    
    printf("%d\n", count);
    return 0;
}
```
## Explicación
Este se trata de replicar un juego determinístico, es decir, el resultado ya esta planteado y es inamovible independientemente de las acciones del usuario.
Para resolverlo, debemos de saber que se trata de un tablero finito 1-D, dónde empiezas en una posición 'x' del tablero, y quieres llegar a una posición 'y' (dónde puede ser que 'x' sea igual a 'y', en ese caso ganas recién entrando).
Como resultado debes de saber a cual de los cuatro resultados posibles llegas y cuantos turnos te demoras:
- Llegas a la casilla objetivo
- Caes del mapa: por la derecha o por la izquierda
- Caes en un ciclo (al ser determinístico y en esta caso depender solo de tu posición, el visitar una casilla ya visitada indica que has caído en un ciclo)
Siempre que no llegues a un resultado definitivo debes de moverte tantos casillas como indique la casilla (cada casilla aparte de su índice, tiene un número que marca cuanto te debes de mover -así como es el número objetivo que se te da-) hacia la derecha (hacia el infinito positivo), este puede ser negativo, lo que te desplazará a la izquierda (hacia el 0).
## Temas relacionados
- [[Secuencias - Python]]
## Link
[1-D Frogger (Easy) – Kattis, Kattis](https://open.kattis.com/problems/1dfroggereasy)