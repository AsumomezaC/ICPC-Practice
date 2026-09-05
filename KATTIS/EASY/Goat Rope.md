#ICPC #Programación #Software 
# Goat Rope
You have a fence post located at the point  in the plane, to which a goat is tethered by a rope. You also have a house, which you model as an axis-aligned rectangle with diagonally opposite corners at the points  and . You want to pick a length of rope that guarantees the goat cannot reach the house.

Determine the minimum distance from the fence post to the house, so that you can make sure to use a shorter rope.

## Input

The input consists of a single line containing six space-separated integers , , , , , and , each in the range .

It is guaranteed that  and , and that  is strictly outside the axis-aligned rectangle with corners at  and .

## Output

Print the minimum distance from the goat’s post to the house, with a relative or absolute error no more than .

|Sample Input 1|Sample Output 1|
|---|---|
|7 3 0 0 5 4|2.0|

|Sample Input 2|Sample Output 2|
|---|---|
|6 0 0 2 7 6|2.0|

|Sample Input 3|Sample Output 3|
|---|---|
|3 -4 -3 -1 -1 2|5.0|
## Código
### [[Python]]
```python
x,y,x1,y1,x2,y2 = map(int, input().split())

def isBetweenIncluded(a,b, value):
    if a>b:
        maxi,mini = a,b
    else:
        maxi,mini = b,a
    if value>=mini and value <=maxi:
        return True, 0
    if value > maxi:
        return False, value-maxi
    else:
        return False, mini-value
        
xNBool, xN = isBetweenIncluded(x1,x2,x)
yNBool, yN = isBetweenIncluded(y1,y2,y)

if xNBool:
    print(yN)
elif yNBool:
    print(xN)
else:
    h = ((xN**2)+(yN**2))**(1/2)
    print(h)
```

Otra versión (recomendada por la IA)
```python
import math

x, y, x1, y1, x2, y2 = map(int, input().split())

min_x, max_x = min(x1, x2), max(x1, x2)
min_y, max_y = min(y1, y2), max(y1, y2)

dx = max(min_x - x, 0, x - max_x)
dy = max(min_y - y, 0, y - max_y)

distancia = math.sqrt(dx**2 + dy**2)

print(distancia)
```
### [[C]] o [[C++]]
Usando la versión mejorada recomendada 
```c
#include <stdio.h>
#include <math.h>

double min(double a, double b){
    double mini = a < b ? a : b;
    return mini;
}

double max(double a, double b){
    double maxi = a < b ? b : a;
    return maxi;
}

int main(void) {
    // Tu código aquí
    double x,y,x1,y1,x2,y2;
    scanf("%lf %lf %lf %lf %lf %lf", &x,&y,&x1, &y1, &x2, &y2);
    
    double maxiX,miniX, maxiY, miniY;
    maxiX = max(x1,x2);
    maxiY = max(y1, y2);
    miniX = min(x1,x2);
    miniY = min(y1, y2);
    
    double finalX = max(0,max(x-maxiX,miniX-x));
    double finalY = max(0,max(y-maxiY,miniY-y));
    
    double res = sqrt(pow(finalX,2)+pow(finalY,2));
    
    printf("%lf\n", res);
    
    return 0;
}
```
## Explicación
Se debe de detectar cual es la distancia tanto en el eje de las 'x' como en el eje de las 'y' entre el punto donde se encuentra el poste como el punto más cercano de la casa (estos están representados por un conjunto incluyente de valores). Una vez conseguidos se debe de aplicar el [[Teorema de Pitágoras]] para obtener el resultado.
## Temas relacionados
- [[Funciones Matemáticas - C]]
## Link
[Goat Rope – Kattis, Kattis](https://open.kattis.com/problems/goatrope)