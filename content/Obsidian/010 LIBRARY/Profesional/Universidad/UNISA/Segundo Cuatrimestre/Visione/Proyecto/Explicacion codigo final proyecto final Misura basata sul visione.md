
## calibration
 `calibration` se utiliza para calibrar una cámara usando imágenes de un patrón conocido (como una cuadrícula de círculos). La calibración de la cámara ayuda a determinar los parámetros internos de la cámara (como la longitud focal y el centro óptico) y los parámetros externos (como la posición y orientación).

### Parámetros
#### Entrada
1. `imageFileNames`: Una lista de nombres de archivos de las imágenes utilizadas para la calibración.
2. `patternDims`: Las dimensiones (filas y columnas) del patrón de calibración.
3. `centerDistance`: La distancia entre los centros de puntos adyacentes en el patrón.
#### Salida
1. `cameraParams`: Los parámetros de la cámara calibrada.
2. `imagesUsed`: Una lista que indica qué imágenes se utilizaron en el proceso de calibración.
3. `estimationErrors`: Errores en la estimación de los parámetros de la cámara.

### Explicación paso a paso

1. **Verificar si se han seleccionado imágenes**
   ```matlab
   if isempty(imageFileNames{1})
       disp('No se seleccionaron imágenes.')
       return
   end
   ```
   Si no se proporcionan imágenes, la función muestra un mensaje y termina.

2. **Detectar el patrón de calibración en las imágenes**
   ```matlab
   detector = vision.calibration.monocular.SymmetricCircleGridDetector();
   [imagePoints, imagesUsed] = detectPatternPoints(detector, imageFileNames, 'PatternDims', patternDims);
   imageFileNames = imageFileNames(imagesUsed);
   ```
   Se crea un detector para encontrar el patrón de calibración en las imágenes. La función `detectPatternPoints` se utiliza para localizar los puntos del patrón en cada imagen. Devuelve los puntos de imagen detectados y una lista que indica qué imágenes se utilizaron.

3. **Leer la primera imagen para obtener el tamaño de la imagen**
   ```matlab
   if ~isempty(imageFileNames)
       originalImage = imread(imageFileNames{1});
       [mrows, ncols, ~] = size(originalImage);
   else
       disp('No hay imágenes válidas para la calibración.')
       return
   end
   ```
   La función lee la primera imagen válida para obtener su tamaño. Si no se encuentran imágenes válidas, termina.

4. **Generar coordenadas del mundo para el patrón**
   ```matlab
   worldPoints = generateWorldPoints(detector, 'PatternDims', patternDims, 'CenterDistance', centerDistance);
   ```
   Genera las coordenadas del mundo real de los puntos del patrón de calibración, asumiendo que el patrón está en un plano plano.

5. **Calibrar la cámara**
   ```matlab
   [cameraParams, imagesUsed, estimationErrors] = estimateCameraParameters(imagePoints, worldPoints, ...
       'EstimateSkew', false, 'EstimateTangentialDistortion', false, ...
       'NumRadialDistortionCoefficients', 2, 'WorldUnits', 'millimeters', ...
       'InitialIntrinsicMatrix', [], 'InitialRadialDistortion', [], ...
       'ImageSize', [mrows, ncols]);
   ```
   La función `estimateCameraParameters` calcula los parámetros de la cámara usando los puntos de imagen detectados y los puntos del mundo generados. Se establecen varias opciones para especificar los detalles del proceso de calibración.

6. **Mostrar resultados de la calibración**
   ```matlab
   disp('Calibración exitosa. Parámetros de la cámara:')
   disp(cameraParams)

   disp('Errores de estimación:')
   disp(estimationErrors)
   ```
   Se muestran los parámetros de la cámara calibrada y los errores de estimación.

### Resumen

- **Detección de patrones**: Detecta un patrón conocido (como una cuadrícula de círculos) en las imágenes.
- **Tamaño de imagen**: Lee la primera imagen para obtener el tamaño para la calibración.
- **Coordenadas del mundo**: Genera coordenadas del mundo real para los puntos del patrón.
- **Calibración de la cámara**: Calcula los parámetros internos y externos de la cámara.
- **Visualización de resultados**: Muestra los parámetros de la cámara calibrada y cualquier error de estimación.



## coinsCounting
`coinsCounting`:
- Cuenta el número de monedas de 1 Euro y 2 Euros en una imagen. 
- Utiliza los radios de los círculos detectados (que representan monedas) y compara estos radios con los tamaños conocidos de las monedas para determinar el tipo de moneda.

### Parámetros
#### Entrada
1. `cameraParams`: Los parámetros calibrados de la cámara.
2. `centers`: Las coordenadas de los centros de los círculos detectados (monedas).
3. `radii`: Los radios de los círculos detectados (monedas).

#### Salida
1. `euro1`: El conteo de monedas de 1 Euro.
2. `euro2`: El conteo de monedas de 2 Euros.

### Explicación paso a paso

1. **Extraer Parámetros de la Cámara**
   ```matlab
   camIntrinsics = cameraParams.Intrinsics;
   R = cameraParams.RotationMatrices;
   t = cameraParams.TranslationVectors;
   tform = rigidtform3d(R(:,:,1), t(1,:));
   ```
   Extrae los parámetros intrínsecos (como la longitud focal) y extrínsecos (rotación y traslación) de la cámara.

2. **Inicializar el Contador de Monedas**
   ```matlab
   euro1 = 0;
   euro2 = 0;
   diam1euro = 23.25;
   diam2euro = 25.75;
   ```
   Inicia los contadores para monedas de 1 Euro y 2 Euros, y define los diámetros de varias monedas en milímetros.

3. **Mostrar Radios en Píxeles**
   ```matlab
   numCircles = numel(radii);
   radiiPixeles = zeros(numCircles, 1);
   for i = 1:numCircles
       radiiPixeles(i) = radii(i);
       disp(['Radio del círculo ', num2str(i), ' en píxeles: ', num2str(radiiPixeles(i))]);
   ```
   Calcula y muestra los radios de los círculos detectados en píxeles.

4. **Convertir Puntos de Imagen a Coordenadas del Mundo Real**
   ```matlab
       imagePoints = [centers(i,1) - radii(i), centers(i,2); 
                      centers(i,1) + radii(i), centers(i,2)];
       worldPoints = img2world2d(imagePoints, tform, camIntrinsics);
       d = worldPoints(2, :) - worldPoints(1, :);
       diameterInMillimeters = hypot(d(1), d(2));
       fprintf("Diámetro medido de una moneda = %0.2f mm\n", diameterInMillimeters);
   ```
   Convierte las coordenadas en píxeles de los círculos detectados a coordenadas del mundo real en milímetros y calcula el diámetro de cada moneda.

5. **Determinar el Tipo de Moneda Basado en el Diámetro**
   ```matlab
       if abs(diameterInMillimeters - diam1euro) < 0.5
           euro1 = euro1 + 1;
           viscircles(centers(i, :), radii(i), 'EdgeColor', 'green', 'LineWidth', 2);
           plot(centers(i,1), centers(i,2), 'g+', 'MarkerSize', 15, 'LineWidth', 2);
           text(centers(i, 1), centers(i, 2), '1 Euro', 'Color', 'green', 'FontSize', 20);
       elseif abs(diameterInMillimeters - diam2euro) < 1.5
           euro2 = euro2 + 1;
           viscircles(centers(i, :), radii(i), 'EdgeColor', 'blue', 'LineWidth', 2);
           plot(centers(i,1), centers(i,2), 'b+', 'MarkerSize', 15, 'LineWidth', 2);
           text(centers(i,1), centers(i,2), '2 Euro', 'Color', 'blue', 'FontSize', 20);
       else
           viscircles(centers(i, :), radii(i), 'EdgeColor', 'red', 'LineWidth', 2);
           plot(centers(i,1), centers(i,2), 'r+', 'MarkerSize', 15, 'LineWidth', 2);
           text(centers(i,1), centers(i,2), 'Cent', 'Color', 'red', 'FontSize', 20);
       end
   end
   hold off
   ```
   Compara el diámetro medido con los diámetros conocidos de las monedas para determinar el tipo de moneda (1 Euro, 2 Euro u otra). Visualiza las monedas detectadas con diferentes colores y etiquetas.

6. **Graficar los Diámetros de Todas las Monedas Detectadas**
   ```matlab
   figure
   plot(coinsDiameter, ones(length(coinsDiameter), 1), '*')
   grid on, grid minor
   xline([diam2euro diam1euro], '-', {'2 euro', '1 euro'})
   ```
   Crea un gráfico de todos los diámetros de las monedas detectadas y marca los diámetros conocidos de diferentes monedas para referencia.

### Resumen

- **Parámetros de la Cámara**: Extrae los parámetros internos y externos de la cámara.
- **Conteo de Monedas**: Inicia contadores para monedas de 1 Euro y 2 Euros.
- **Cálculo de Diámetros**: Convierte las coordenadas de la imagen a coordenadas del mundo real y calcula los diámetros de las monedas.
- **Clasificación de Monedas**: Compara los diámetros medidos con los diámetros conocidos para clasificar las monedas.
- **Visualización**: Muestra las monedas detectadas y sus diámetros.


## ImageProcessing
1. Esta función de MATLAB `imageProcessing` procesa una imagen para detectar círculos (como monedas) dentro de ella. 
2. Convierte la imagen a escala de grises, luego a binario, elimina ruido y, finalmente, detecta círculos.

### Parámetro
#### Entrada
1. `image`: La imagen de entrada a procesar.

#### Salida
1. `centers`: Los centros de los círculos detectados.
2. `radii`: Los radios de los círculos detectados.

### Explicación paso a paso

1. **Convertir la imagen a escala de grises**
   ```matlab
   grayImage = rgb2gray(image);
   ```
   Eliminando la información de color pero manteniendo los niveles de brillo.

2. **Convertir la imagen en escala de grises a imagen binaria**
   ```matlab
   level = graythresh(grayImage);
   BW = imbinarize(grayImage, level);
   ```
   La función calcula un umbral global utilizando el método de Otsu y convierte la imagen a una imagen binaria (blanco y negro).

3. **Limpiar la imagen eliminando ruido y rellenando huecos**
   ```matlab
   BW2 = imfill(BW, 'holes');
   BW2 = bwareaopen(BW2, 100);
   ```
   - Este paso rellena cualquier hueco en la imagen binaria (convierte áreas negras dentro de áreas blancas a blanco)
   - Elimina objetos pequeños con menos de 100 píxeles.

4. **Aplicar método de gradiente a la imagen binaria**
   ```matlab
   sobelx = [-1 0 1; -2 0 2; -1 0 1];
   sobely = sobelx';
   CC = grayImage > graythresh(grayImage) * 255;
   I_CC = 255 * CC;
   Hy = imfilter(I_CC, sobely);
   Hx = imfilter(I_CC, sobelx);
   H = Hx.^2 + Hy.^2;
   ```
   - Este paso utiliza filtros de Sobel para detectar bordes en la imagen binaria, calculando el gradiente (cambio de intensidad) en direcciones horizontales y verticales.

5. **Detección de bordes utilizando el método de Canny**
   ```matlab
   L = edge(H, 'canny');
   SE = strel('disk', 2);
   CCL = imclose(CC, SE);
   BB = edge(CCL, 'canny');
   ```
   - Este paso aplica el método de detección de bordes de Canny para encontrar los bordes de los objetos en la imagen.
   - Se utiliza una operación de cierre morfológico para cerrar pequeñas brechas y unir puntos adyacentes.

6. **Detección de círculos**
   ```matlab
   [centers, radii] = imfindcircles(BB, [20 200], 'Sensitivity', 0.8);
   ```
   - Este paso detecta círculos en la imagen procesada con una sensibilidad especificada, permitiendo la detección de círculos tanto regulares como ligeramente irregulares.

### Resumen

- **Conversión a escala de grises**: Convierte la imagen a tonos de gris, reteniendo información de brillo.
- **Conversión binaria**: Convierte la imagen en escala de grises a blanco y negro usando un umbral calculado.
- **Eliminación de ruido**: Limpia la imagen rellenando huecos y eliminando objetos pequeños.
- **Detección de bordes**: Detecta bordes en la imagen binaria usando métodos de gradiente.
- **Detección de círculos**: Encuentra círculos en la imagen procesada.

