# Exercice 1
## Question 1
- Reprendre le cours (voir cm7 quand il sera repris)
## Question 2
**On a pas besoin de chainage statique pour un programme en C**

### Programme
```C
#include <stdio.h>

int ext,b ,x;
int F2(int *x, int *y);

void F1(int x, int *y)
{
	x=x*2;
	b=x*10;
	*y=*y*3;
	printf("valeur de *y : %d \n", *y);
	printf("valeur de b : %d \n",b);
	z=F2(&x,y)-b;
	printf("valeur de z : %d \n",z);

}

int F2(int *x, int *y)
{
	*x=*x*10;
	*y=*y*100;
	printf("Valeur de retour de F2 : %d\n", b + *x + *y);
	// POINT 1
	return(b + *x+*y);

}
void main()
{ int b;

 b=2;
 ext=1;
 z=3;
 F1(ext,&b);

}

```
![[la grosse pile]]
# Exercice 2
```Ocaml
Programme EXEMPLE 2

A,B,C : entier

Procedure P1(var X: entier; Y: entier)
	X:=X*2
	Y:=Y*2  /* POINT 1 */
	P2(X,Y)
fin_P1

Procedure P2(var R: entier; S : entier)
	Procedure P3(var V: entier; S: entier)
		V:=V*3
		S:=S*3  /* POINT 2 */
		C:=R*V
	fin_P3
	R:=R+S /* POINT 3 */
	P3(S,R)
fin_P2

debut_EXEMPLE2

A:=10; B:=20; C:=30 /* POINT 4 */
P1(A,B)   /* POINT 5*/
```
![[La deuxieme grosse pile]]

