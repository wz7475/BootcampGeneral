# Wprowadzenie do Algebry Liniowej
[Link do serii 3Blue1Brown](https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)

<!-- Spis treści dla lepszej nawigacji w GitHub Preview -->
## Spis treści
- [Wektory](#wektory)
- [Macierze](#macierze)
- [Operacje na macierzach](#operacje-na-macierzach)
  - [Mnożenie macierzy przez skalar](#mnożenie-macierzy-przez-skalar)
  - [Dodawanie macierzy](#dodawanie-macierzy)
  - [Mnożenie macierzy](#mnożenie-macierzy)
  - [Transpozycja macierzy](#transpozycja-macierzy)
- [Norma wektora](#norma-wektora)
- [Standardowy iloczyn skalarny](#standardowy-iloczyn-skalarny)

**Algebra liniowa** to dziedzina matematyki zajmująca się badaniem przestrzeni liniowych oraz operacji na wektorach i macierzach. W uczeniu maszynowym algebra liniowa jest kluczowa, ponieważ większość operacji na danych i modelach można wyrazić jako operacje na wektorach i macierzach. Na przykład dane w formie tabeli możemy traktować jako macierz, a parametry modelu jako wektory/macierze.


## Wektory

**Wektor** to uporządkowany zbiór liczb, które reprezentują punkt w przestrzeni. Wektory możemy traktować jako listy liczb, które możemy wykorzystywać do opisywania różnych cech lub wartości.

**Notacja:**
Wektor oznaczamy jako kolumnę liczb, np.:
$$
\mathbf{v} = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix}
$$
gdzie $ v_1, v_2, \ldots, v_n $ to elementy wektora.

**Przykład wektora 3-wymiarowego:**
Weźmy wektor:

$$
\mathbf{v} = \begin{bmatrix} 2 \\ 3 \\ -1 \end{bmatrix}
$$

Ten wektor można traktować jako punkt w 3-wymiarowej przestrzeni, opisujący położenie w osi $ x = 2 $, $ y = 3 $, $ z = -1 $.


## Macierze

**Macierz** to tablica liczb, która składa się z wierszy i kolumn. Każdy element macierzy jest oznaczany jako $ a_{ij} $, gdzie $ i $ oznacza numer wiersza, a $ j $ numer kolumny.

**Notacja:**
Macierz $ \mathbf{A} $ o wymiarach $ m \times n $ można zapisać jako:

$$
\mathbf{A} = \begin{bmatrix} a_{11} & a_{12} & \dots & a_{1n} \\ a_{21} & a_{22} & \dots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \dots & a_{mn} \end{bmatrix}
$$

**Przykład macierzy 2×3:**

$$
\mathbf{A} = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}
$$

W uczeniu maszynowym macierze często reprezentują zestawy danych – każdy wiersz może być jednym przykładem (rekordem), a każda kolumna cechą.


## Operacje na macierzach

### Mnożenie macierzy przez skalar

Załóżmy, że mamy skalar $ k $ oraz macierz $ \mathbf{A} $ o wymiarach $ m \times n $:

$$
\mathbf{A} = \begin{bmatrix} a_{11} & a_{12} & \dots & a_{1n} \\ a_{21} & a_{22} & \dots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \dots & a_{mn} \end{bmatrix}
$$

Aby pomnożyć macierz $ \mathbf{A} $ przez skalar $ k $, mnożymy każdy element $ a_{ij} $ przez $ k $:

$$
k \cdot \mathbf{A} = \begin{bmatrix} k \cdot a_{11} & k \cdot a_{12} & \dots & k \cdot a_{1n} \\ k \cdot a_{21} & k \cdot a_{22} & \dots & k \cdot a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ k \cdot a_{m1} & k \cdot a_{m2} & \dots & k \cdot a_{mn} \end{bmatrix}
$$

**Przykład**

Rozważmy skalar $ k = 3 $ oraz macierz:

$$
\mathbf{A} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}
$$

Aby pomnożyć macierz $ \mathbf{A} $ przez skalar $ 3 $, wykonujemy następujące operacje:

$$
\begin{aligned}
3 \cdot \mathbf{A}
  &= 3 \cdot \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} \\
  &= \begin{bmatrix} 3 \cdot 1 & 3 \cdot 2 \\ 3 \cdot 3 & 3 \cdot 4 \end{bmatrix} \\
  &= \begin{bmatrix} 3 & 6 \\ 9 & 12 \end{bmatrix}
\end{aligned}
$$

---

### Dodawanie macierzy

Dwie macierze o tych samych wymiarach można dodawać, dodając elementy znajdujące się na tych samych pozycjach. Jeśli macierze mają różne wymiary, operacja dodawania nie jest możliwa.

**Przykład dodawania macierzy:**
Jeśli mamy macierze:

$$
\mathbf{A} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}, \quad \mathbf{B} = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}
$$

to ich suma wynosi:

$$
\mathbf{A} + \mathbf{B} = \begin{bmatrix} 1+5 & 2+6 \\ 3+7 & 4+8 \end{bmatrix} = \begin{bmatrix} 6 & 8 \\ 10 & 12 \end{bmatrix}
$$

---

### Mnożenie macierzy

Załóżmy, że mamy dwie macierze:
1. Macierz $ \mathbf{A} $ o wymiarach $ m \times n $, czyli $ m $ wierszy i $ n $ kolumn.
2. Macierz $ \mathbf{B} $ o wymiarach $ n \times p $, czyli $ n $ wierszy i $ p $ kolumn.

Ważne jest, aby liczba kolumn w pierwszej macierzy (tu: $ \mathbf{A} $) była równa liczbie wierszy w drugiej macierzy (tu: $ \mathbf{B} $). W przeciwnym wypadku mnożenie nie będzie możliwe. Wynikiem mnożenia macierzy $ \mathbf{A} $ i $ \mathbf{B} $ jest nowa macierz $ \mathbf{C} $ o wymiarach $ m \times p $.

#### Jak obliczyć elementy macierzy wynikowej?

Każdy element $ c_{ij} $ w macierzy wynikowej $ \mathbf{C} $ jest obliczany jako iloczyn skalarów wiersza $ i $-tego z macierzy $ \mathbf{A} $ oraz kolumny $ j $-tej z macierzy $ \mathbf{B} $.

Formalnie:

$$
c_{ij} = \sum_{k=1}^{n} a_{ik} \cdot b_{kj}
$$

gdzie:
- $ a_{ik} $ oznacza element w $ i $-tym wierszu i $ k $-tej kolumnie macierzy $ \mathbf{A} $,
- $ b_{kj} $ oznacza element w $ k $-tym wierszu i $ j $-tej kolumnie macierzy $ \mathbf{B} $,
- $ c_{ij} $ to element w $ i $-tym wierszu i $ j $-tej kolumnie macierzy wynikowej $ \mathbf{C} $.

#### Przykład mnożenia macierzy

Weźmy konkretne macierze, aby zobaczyć, jak wygląda ten proces:

Załóżmy, że mamy:

$$
\mathbf{A} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} \quad (\text{macierz } 2 \times 2)
$$

$$
\mathbf{B} = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix} \quad (\text{macierz } 2 \times 2)
$$

Chcemy pomnożyć $ \mathbf{A} $ przez $ \mathbf{B} $ i uzyskać macierz $ \mathbf{C} = \mathbf{A} \cdot \mathbf{B} $.

**Krok 1**: Oblicz element $ c_{11} $
- Bierzemy pierwszy wiersz z $ \mathbf{A} $: $ [1, 2] $
- Bierzemy pierwszą kolumnę z $ \mathbf{B} $: $ \begin{bmatrix} 5 \\ 7 \end{bmatrix} $
- Obliczamy iloczyn skalarów: $ 1 \cdot 5 + 2 \cdot 7 = 5 + 14 = 19 $
- Wstawiamy wynik na pozycję $ c_{11} $ w macierzy $ \mathbf{C} $.

**Krok 2**: Oblicz element $ c_{12} $
- Bierzemy pierwszy wiersz z $ \mathbf{A} $: $ [1, 2] $
- Bierzemy drugą kolumnę z $ \mathbf{B} $: $ \begin{bmatrix} 6 \\ 8 \end{bmatrix} $
- Obliczamy iloczyn skalarów: $ 1 \cdot 6 + 2 \cdot 8 = 6 + 16 = 22 $
- Wstawiamy wynik na pozycję $ c_{12} $ w macierzy $ \mathbf{C} $.

Krok 3 oraz 4 przebiegają w analogiczny sposób.

Po wykonaniu wszystkich kroków macierz wynikowa $ \mathbf{C} $ wygląda następująco:

$$
\mathbf{C} = \begin{bmatrix} 19 & 22 \\ 43 & 50 \end{bmatrix}
$$

---

### Transpozycja macierzy

Transpozycja macierzy polega na zamianie wierszy z kolumnami. Transponowaną macierz oznaczamy symbolem $ \mathbf{A}^T $.

**Przykład transpozycji macierzy:**
Jeśli mamy macierz:

$$
\mathbf{A} = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}
$$

to jej transpozycja to:

$$
\mathbf{A}^T = \begin{bmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{bmatrix}
$$


## Norma wektora

**Norma** wektora to liczba opisująca jego długość. Najczęściej używana norma to **norma euklidesowa**, która jest odległością punktu (wektora) od początku układu współrzędnych.

**Wzór na normę euklidesową:**
Dla wektora $ \mathbf{v} = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix} $:
$$
||\mathbf{v}||_{2} = \sqrt{v_1^2 + v_2^2 + \dots + v_n^2}
$$

**Przykład:**
Dla wektora $ \mathbf{w} = \begin{bmatrix} 3 \\ 4 \end{bmatrix} $:
$$
||\mathbf{w}||_{2} = \sqrt{3^2 + 4^2} = 5
$$


## Standardowy iloczyn skalarny

**Standardowy iloczyn skalarny** to operacja na dwóch wektorach o tej samej liczbie wymiarów, której wynik jest liczbą (skalarem). Iloczyn skalarny wektorów $ \mathbf{u} = \begin{bmatrix} u_1 \\ u_2 \\ \dots \\ u_n \end{bmatrix} $ oraz $ \mathbf{v} = \begin{bmatrix} v_1 \\ v_2 \\ \dots \\ v_n \end{bmatrix} $ jest zdefiniowany jako:

$$
\mathbf{u} \cdot \mathbf{v} = u_1 v_1 + u_2 v_2 + \dots + u_n v_n = \sum_{i=1}^{n} u_i v_i
$$

Iloczyn skalarny wyraża miarę podobieństwa kierunku między wektorami, a jego wynik może być dodatni, ujemny lub równy zero.

**Przykład:**
Rozważmy wektory:

$$
\mathbf{u} = \begin{bmatrix} 1 \\ 3 \end{bmatrix}, \quad \mathbf{v} = \begin{bmatrix} 4 \\ 2 \end{bmatrix}
$$

Iloczyn skalarny $ \mathbf{u} \cdot \mathbf{v} $ wynosi:

$$
\mathbf{u} \cdot \mathbf{v} = (1 \cdot 4) + (3 \cdot 2) = 4 + 6 = 10
$$

**Właściwości iloczynu skalarnego:**
1. Iloczyn skalarny jest przemienny: $ \mathbf{u} \cdot \mathbf{v} = \mathbf{v} \cdot \mathbf{u} $.
2. Iloczyn skalarny dwóch ortogonalnych (prostopadłych) wektorów wynosi zero.

**Interpretacja geometryczna:**
Iloczyn skalarny dwóch wektorów $ \mathbf{u} $ i $ \mathbf{v} $ można również wyrazić jako:

$$
\mathbf{u} \cdot \mathbf{v} = ||\mathbf{u}|| \, ||\mathbf{v}|| \cos \theta
$$

gdzie $ ||\mathbf{u}|| $ i $ ||\mathbf{v}|| $ to normy (długości) wektorów, a $ \theta $ to kąt między wektorami. Dzięki temu możemy mierzyć, jak bardzo wektory są skierowane w tę samą stronę:
- Jeśli $ \theta = 0^\circ $, iloczyn skalarny osiąga wartość maksymalną.
- Jeśli $ \theta = 90^\circ $, iloczyn skalarny wynosi zero, co oznacza, że wektory są prostopadłe.
- Jeśli $ \theta = 180^\circ $, iloczyn skalarny jest ujemny, co oznacza, że wektory mają przeciwny kierunek.