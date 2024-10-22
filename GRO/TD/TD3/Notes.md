# Feuille 2 exercice 3
## Q1
### Données
Plateau riche : 
- Prix $P_r$
- Oursin $n_1^r$
- Palourde $n_2^r$
- Huître $n_3^r$
Plateau simple :
- Prix $P_s$
- Oursin $n_1^s$
- Palourde $n_2^s$
- Huître $n_3^{s}$
Disponibilité
- $k_1$ Oursins
- $k_2$ Palourdes
- $k_3$ Huîtres
### Variables
- $x_r$ Nombre de plateaux riches
- $x_s$ Nombre de plateaux simples
- $x_r x_s \in N$
### Objectif 
- Maximiser le bénéfice $F(x_r,x_s)=P_rx_r+P_xs_s$
### Contraintes
$$\begin{cases} n_1^rx_r+n_1^sx_s \le k_1 \quad \text{oursins} \\n_2^rx_r+n_2^sx_s \le k_2 \quad \text{palourdes} \\
n_3^rx_r+n_3^sx_s \le k_3 \quad \text{huitres} \\
\end{cases}$$
## Q2
### Variables
- $y_1$ Prix Oursins
- $y_2$ Prix Palourdes
- $y_3$ Prix Huîtres
### Objectif 
- Minimiser les couts $G(y_1,y_2,y_3)=k_1y_1+k_2y2+k_3y_3$
### Contraintes
$$\begin{cases} n_1^ry_1+n_2^ry_2 + n_3^ry_3 \ge P_r
\\n_2^sy_1+n_2^sy_2+n_3^sy_3 \ge P_s \\
y_1,y_2,y_3 \ge 0 \\
\end{cases}$$
### Problème primal
$$max F(x)=c^Tx, x=\begin{pmatrix}
x_r \\
x_s
\end{pmatrix}
c=\begin{pmatrix}
P_r \\
P_s
\end{pmatrix}$$
$$\begin{cases}Ax\le b , A=\begin{pmatrix}
n_1^r & n_1^s \\
n_2^r & n_2^s \\
n_3^r & n_3^s
\end{pmatrix}, b=\begin{pmatrix}
k_1 \\
k_2 \\
k_3
\end{pmatrix}\\
x \ge 0\\
\text{x entiers}\end{cases}$$
### Problème dual
$$min[G(y)=b^Ty],y=\begin{pmatrix}
y_1 \\
y_2 \\
y_3
\end{pmatrix}$$ $$\begin{cases} A^Ty \ge c \\
y \ge 0
\end{cases}$$
### a)
$$f(x) = c^Tx \le (A^Ty)^T$$
$$(A^Ty)^T=y^TAx \le y^Tb$$
$$y^Tb=b^Ty=g(y)$$
Donc, f(x)$\le$g(y)
#### Indication
$$\xi = A^Ty -c \ge 0, \mu = b  - Ax \ge 0$$
$$0\le \mu^Ty+x^T\xi = g(y)-f(x)$$
Soit : 
$$x^*\in C_p, y^*\in C_D |f(x^*)=g(y^*)$$
On a :
$$f(x)\le g(y), \forall x \in C_p , \forall y \in C_D$$
Donc :
$$f(x) \le g(y^*) = f(x^*), \forall x \in C_p (x^* \in C_p)$$
Donc : 
$$f(x^*)=max_{x \in C_p}f(x)$$
De même
$$g(^*y)\le g(y) , \forall y \in C_D$$
Donc :
$$g(y^*)=min_{y \in C_D}g(y)$$
# Feuille 3 exercice 1
## Variables
- $x_i \quad  \text{quantité de produit}\quad P_i\quad \text{fabriqué},i\in[1,4],x_i\ge0$
## Objectif
- $max_{x_1,x_2,x_3,x_4}[F(x)=50x_1+40x_2+70x_3+80x_4]$
	- miaou :3
		- miaou
		- miaou
		- miaou
		miaou :3
## Contraintes
$$\begin{cases}2x_1+4x_2+8x_3+6x_4\le160\\
10x_1+8x_2+6x_3+10x_4\le 160\\
x_1+x2+x_3+x_4 \le 20\\
x_1,x_2,x_3,x_4\ge 0
\end{cases}$$
### Solution de base réalisable (Contraintes Ax=b, x>=0)
$$A=(A_B|A_H), A_B\quad \text{matrice carrée inversible(m*m)}A_H \quad \text{matrice hors base}$$
$$x=(x_b|x_h)^T, x_b \quad \text{variables de base}\quad x_h\quad \text{variables hors base}$$
- Avec $x_h=0$ (**solutions de base**)
$$A_x=A_Bx_B+A_Hx_H=b$$
Donc : $$x_B=A_B^{-1}(b-A_Hx_H)$$
### Méthode des dictionnaires
- Variable entrante
- Variable sortante
- **On exprime tout en fonction des variables hors base** $x_H$
$F(x)=c^Tx=c^T_Bx_B+c_H^Tx_H$
	 $= C_B^TA^{-1}_B(b-A_Hx_H)+c_H^Tx_H$
	 $=c_B^TA^{-1}_Bb+[c_H^T-c_B^TA^{-1}_BA_H]x_H$
#### Forme standard
$$max F(x)_{x=(x_1,x_2,x_3,x_4,e_1,e_2,e_3)}=50x_1+40x_2+70x_3+80x_4$$	