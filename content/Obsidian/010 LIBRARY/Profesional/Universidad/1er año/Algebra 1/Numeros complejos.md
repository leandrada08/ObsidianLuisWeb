# NÚMEROS COMPLEJOS

## Definición de Número Complejo
Un **número complejo** es un número de la forma:

$$
z = a + bi
$$

donde $a, b \in \mathbb{R}$, e $i$ es la **unidad imaginaria**, con la propiedad:

$$
i^2 = -1
$$

- $a$ es la **parte real** de $z$.
- $b$ es la **parte imaginaria** de $z$.

## Operaciones con Números Complejos

### 1. Suma y Resta
Dados dos números complejos $z_1 = a + bi$ y $z_2 = c + di$:

- **Suma**: $z_1 + z_2 = (a + c) + (b + d)i$
- **Resta**: $z_1 - z_2 = (a - c) + (b - d)i$

### 2. Multiplicación
La **multiplicación** de dos números complejos $z_1 = a + bi$ y $z_2 = c + di$ se realiza distribuyendo los términos:

$$
z_1 \cdot z_2 = (ac - bd) + (ad + bc)i
$$

### 3. División
La **división** de dos números complejos se realiza multiplicando por el conjugado del denominador:

$$
\frac{z_1}{z_2} = \frac{(a + bi)(c - di)}{c^2 + d^2} = \frac{(ac + bd) + (bc - ad)i}{c^2 + d^2}
$$

## Forma Binómica
La **forma binómica** de un número complejo es la más común y se expresa como:

$$
z = a + bi
$$

donde $a$ es la parte real y $b$ es la parte imaginaria.

## Conjugado de un Número Complejo
El **conjugado** de un número complejo $z = a + bi$ se denota como $\overline{z}$ y se define como:

$$
\overline{z} = a - bi
$$

### Propiedades del Conjugado
1. **Producto**: $z \cdot \overline{z} = a^2 + b^2$
2. **Suma**: $\overline{z_1 + z_2} = \overline{z_1} + \overline{z_2}$
3. **Multiplicación**: $\overline{z_1 \cdot z_2} = \overline{z_1} \cdot \overline{z_2}$

## Módulo de un Número Complejo
El **módulo** de un número complejo $z = a + bi$ es la **distancia** desde el origen hasta el punto $(a, b)$ en el plano complejo, y se denota como $|z|$:

$$
|z| = \sqrt{a^2 + b^2}
$$

### Propiedades del Módulo
1. **Producto**: $|z_1 \cdot z_2| = |z_1| \cdot |z_2|$
2. **División**: $\left| \frac{z_1}{z_2} \right| = \frac{|z_1|}{|z_2|}$
3. **Conjugado**: $|z| = |\overline{z}|$

## Forma Polar
La **forma polar** de un número complejo se utiliza para expresar $z$ en términos de su módulo y su ángulo (argumento) $\theta$:

$$
z = r (\cos \theta + i \sin \theta)
$$

donde:
- $r = |z|$ es el módulo.
- $\theta = \arg(z)$ es el **argumento** de $z$, que representa el ángulo entre el vector $z$ y el eje real positivo en el plano complejo.

El argumento puede ser calculado mediante:

$$
\theta = \tan^{-1}\left( \frac{b}{a} \right)
$$

### Forma Polar Completa
A menudo se denota también como:

$$
z = r \text{cis}(\theta)
$$

donde $\text{cis}(\theta) = \cos(\theta) + i\sin(\theta)$.

## Potencia y Radicación de Números Complejos

### 1. Potencia (Fórmula de De Moivre)
La **Fórmula de De Moivre** se usa para calcular potencias de números complejos en forma polar:

$$
z^n = \left( r (\cos \theta + i \sin \theta) \right)^n = r^n \left( \cos(n\theta) + i \sin(n\theta) \right)
$$

### 2. Radicación
Para calcular la **n-ésima raíz** de un número complejo $z = r \text{cis}(\theta)$:

$$
z^{1/n} = r^{1/n} \text{cis}\left( \frac{\theta + 2k\pi}{n} \right), \quad k = 0, 1, 2, \ldots, n-1
$$

Esto indica que hay $n$ raíces diferentes de un número complejo.

## Forma Exponencial
La **forma exponencial** de un número complejo se basa en la identidad de Euler:

$$
e^{i\theta} = \cos(\theta) + i\sin(\theta)
$$

Por lo tanto, un número complejo $z$ puede expresarse como:

$$
z = r e^{i\theta}
$$

donde $r$ es el módulo y $\theta$ es el argumento de $z$. Esta forma es especialmente útil para operaciones como la multiplicación y división, y para representar la oscilación en aplicaciones de ingeniería.

### Propiedades de la Forma Exponencial
- **Producto**: $z_1 z_2 = r_1 r_2 e^{i(\theta_1 + \theta_2)}$
- **División**: $\frac{z_1}{z_2} = \frac{r_1}{r_2} e^{i(\theta_1 - \theta_2)}$
- **Potencias**: Utilizando la Fórmula de De Moivre, $z^n = (r e^{i\theta})^n = r^n e^{in\theta}$

### Ejemplo de Uso de la Forma Exponencial
Para $z_1 = 2e^{i\pi/4}$ y $z_2 = 3e^{i\pi/6}$:

$$
z_1 z_2 = (2 \times 3)e^{i(\pi/4 + \pi/6)} = 6e^{i5\pi/12}
$$

Esto muestra cómo la forma exponencial simplifica la multiplicación de números complejos.

