## Errori di Riproiezioni


#### Concetto di Errore di Riproiezione
Después de realizar la calibración, es decir, estimar la matriz $P$, se proyectan los puntos $\mathbf{M}_i$ sobre el plano del sensor usando $\mathbf{m}_i = P \mathbf{M}_i$. En condiciones ideales, $\mathbf{m}_i$ coincide con las coordenadas en píxeles observadas $\mathbf{m}_i$. Sin embargo, debido a la incertidumbre de los datos y limitaciones del modelo pin-hole, hay una discrepancia.

#### Definición del Error de Riproiezione
Para evaluar la calidad de la calibración, se calcula el error de riproiezione como la suma de las distancias euclideas entre $\mathbf{m}_i$ y $\hat{\mathbf{m}}_i$ (la riproiezione de $\mathbf{M}_i$):

$$ e_{\text{ripro}} = \sum_{i=1}^{N} \|\mathbf{m}_i - \hat{\mathbf{m}}_i\| $$

#### Error de Riproiezione Medio
Para hacer el error independiente del número de puntos $N$ y más interpretable en términos de píxeles, se utiliza el error de riproiezione medio:

$$ e_{\text{ripro,medio}} = \frac{1}{N} \sum_{i=1}^{N} \|\mathbf{m}_i - \hat{\mathbf{m}}_i\| $$

#### Ejemplo de Cálculo del Error de Riproiezione
A continuación se muestra un ejemplo de cómo calcular el error de riproiezione usando MATLAB:

```matlab
% Carica i punti da file
load -ASCII coordassolute.txt
load -ASCII coordpixelDX.txt

% Determina il numero di punti caricati
N = size(coordassolute, 1);

% Converte i punti in coordinate omogenee
M = [coordassolute ones(N, 1)];
m = [coordpixelDX ones(N, 1)];

% Prepara la matrice di coefficienti del sistema
A = zeros(2 * N, 12);
for i = 1:N
    A(2 * i - 1, :) = [zeros(1, 4) -m(i, 3) * M(i, :) m(i, 2) * M(i, :)];
    A(2 * i, :) = [m(i, 3) * M(i, :) zeros(1, 4) -m(i, 1) * M(i, :)];
end

% Risolve il sistema Ap = 0 con la scomposizione SVD
[U, S, V] = svd(A);

% La soluzione p è pari all'ultima colonna (la 12esima) di V
p = V(:, 12);

% Si costruisce la matrice di proiezione prospettica
P = [p(1:4)'; p(5:8)'; p(9:12)'];

% Si riproiettano i punti M
mr = zeros(N, 3);
mrc = zeros(N, 2);
for i = 1:N
    mr(i, 1:3) = P * M(i, 1:4)';
    % Passaggio coordinate cartesiane
    mrc(i, 1:2) = [mr(i, 1) / mr(i, 3) mr(i, 2) / mr(i, 3)];
end

% Calcola l'errore geometrico (di riproiezione)
e = mean(sqrt(sum((coordpixelDX - mrc).^2, 2)));
disp(['Errore di riproiezione medio: ', num2str(e)]);
```

#### Uso del Error de Riproiezione para Refinar la Calibración
El error de riproiezione puede usarse como una función objetivo para mejorar la calibración mediante algoritmos de minimización iterativa, como el algoritmo de Levenberg-Marquardt, utilizando la solución DLT como inicial.

#### Formulación del Problema de Minimización
El problema de minimización se formula como:

$$ \min_P \sum_{i=1}^{N} d(\mathbf{m}_i, \hat{\mathbf{m}}_i) $$

Donde $d$ es la distancia euclidea y $\hat{\mathbf{m}}_i = P \mathbf{M}_i$.

#### Vector de Parámetros
En lugar de estimar directamente los elementos de $P$, se puede usar un vector de parámetros que define $P$ de forma más eficiente:

$$ \alpha = [f_x, f_y, u_0, v_0, \theta, \phi, \psi, t_x, t_y, t_z] $$

Este vector puede incluir también parámetros de distorsión de la lente.

