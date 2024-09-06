La distancia de Levenshtein, distacia de edicion o distancia entre palabras es el  numero minimo de operaciones requeridas pra transformas una cadena de caracteres en otra
Esta distancia es una generalizacion de la [[Distancia Hamming]] para cadenas de distinta longitud

### Usos
Se lo utiliza para la deteccion de errores en textos


### Calculo
![[Pasted image 20221225230230.png]]

### Implementacion en Python
```python
def distance(str1, str2):
  d=dict()
  for i in range(len(str1)+1):
     d[i]=dict()
     d[i][0]=i
  for i in range(len(str2)+1):
     d[0][i] = i
  for i in range(1, len(str1)+1):
     for j in range(1, len(str2)+1):
        d[i][j] = min(d[i][j-1]+1, d[i-1][j]+1, d[i-1][j-1]+(not str1[i-1] == str2[j-1]))
  return d[len(str1)][len(str2)]
```