# Analyse syntaxique descendante
[[TRAD 1/TD/TD1 et TD2/Notes|Voir TD 1]]
## Question 3
### Grammaire
$$G\begin{cases}
A\rightarrow V|(f_1A X \\
X \rightarrow .f_2A)f_5|S)f5 \\
S\rightarrow , f_4A S | \varepsilon  f_7\\ 
V\rightarrow entier f_3| nil f_4\\ 
\end{cases}$$

### Fonctions sémantiques
- $f_1=$ écrire ("(")
- $f_2=$ écrire (".")
- $f_3=$ écrire ("entier")
- $f_4=$ écrire ("nil")
- $f_5=$ écrire (")")
- $f_6=$ écrire (".(")
- $f_7=$ écrire (".nil")
# Même principe, avec une analyse syntaxique ascendante
## Notation binaire
$$G\begin{cases}
A' \rightarrow A \quad f_4 \begin{cases}x=depiler() \\
écrire(x)
\end{cases} \\
A\rightarrow V\\
\quad \quad(A.A) \quad f_3 \begin{cases}x_1=depiler()\\
x_2=depiler\\
empiler("(x_2.x_1)")\end{cases} \\
\quad \quad(A S) \quad f_3 \\
S\rightarrow , A S \quad f_3 \\
\quad \quad \varepsilon \quad f_2  \\ 
V\rightarrow entier \quad f_1=empiler(entier)\\
\quad \quad nil \quad f_2 = empiler(nil)\\ 
\end{cases}$$
## Deuxième exemple (grammaire recursive gauche)
### Grammaire
$$ \begin{cases}S' \rightarrow A  \quad f_0 \begin{cases}x=depiler() \\
écrire(x)
\end{cases}\\
A \rightarrow V\\
\quad \quad (C)\\
C \rightarrow A.A \quad f_3 \begin{cases}x_1=depiler()\\
x_2=depiler\\
empiler("(x_2.x_1)")\end{cases} \\
\quad \quad L  \quad f_5\\
L \rightarrow  A \quad f_4\\
\quad \quad L,A\\
V \rightarrow entier \quad f_1=empiler(entier)\\
\quad \quad nil \quad f_2 = empiler(nil) \end{cases}
$$
### $f_4$ et  $f_5$
$$f_4=\begin{cases}x= depiler\\
empiler ("\#") \quad \text{note : \# correspond au marqueur de début de liste}\\
empiler (x)
\end{cases}$$ $$f_5=\begin{cases}x_2=nil\\\text{tant que sommet pile != "\#"}\begin{cases}x_1 =depiler()\\
x_2 = "(x_1.x_2)"
\end{cases} \\
\text{fin tant que}\\
dépiler\\
empiler(x_2)
\end{cases}$$
### Exemple d'arbre syntaxique correspondant
![[TRAD 1/TD/TD4/Arbre syntaxique]]


