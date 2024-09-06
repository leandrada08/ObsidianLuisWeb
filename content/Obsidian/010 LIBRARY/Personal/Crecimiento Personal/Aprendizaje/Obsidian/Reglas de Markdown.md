Es un lenguaje de marcado ligero, permite enrriqueser un texto plano, mendiante la interpretacion de simbologia de lenguaje, de esta manera permite que el texto sea mas agradable
# Reglas markdown
# Titulo General
## Titulo secundario 
### Titulo Terciario
#### Titulo cuarto

## formato texto
**Negrita**
*Cursiva*
***Negrita y cursiva***
___Negrita y cursiva___ ^8867c1

[[MARKDOWN]] no permite subrayado para evitar confundir enlanses y no permite espacios en blanco

Se puede tachar con 2 veces ~~ y se lo termina con doble ~~

[[MARKDOWN]] Permite el resaltado con doble == antes y despues

## Divisores y presentaciones

Divisores de guiones con 3 guiones altos 

---
Presentacion 1
Estos guiones tambien permiten armar presentaciones, donde cada diapositiva seria lo presentado entre los divisores

---
Presentacion 2

---

## Citas

simbolo de mayor que y la cita

>Lo que importa no es lo que sabes sino lo que haces con lo que sabes

lista to do con - [ ] 
- [ ] comprar pan
- [x] Ya compre pan

## Listas
Sin numerar
	Creamos con guion
	- hola
	- Soy 
	- piola

Numeradas
	Solo con el numero y 1 punto
	1. Hola
	2. Soy
		1. Lo mas piola
		2. Lo mas crack


## [[Anexos Obsidian]]

Los anexos aunque son algo separado del lenguaje MARKSOWN son algo que se usan mucho, es lo por ellos que dedicamos una nota completa de esta
## Bloques de codigo

Hay que inluir 3 tildes luego aclarar el leguanje y de ahi comenzar a escribir, tambien se cierra con 3 comillas

```js
function fancyAlert(arg){
	if(arg){
		$.facebox({div})
	}
}
```

## Comentarios que no compilan

%% hola putos curiosos %%

### Incluir caracteres para que markdown no compile
añadir \[barra invertida adelante del caracter\]

## Tablas
|Nombre|Valor|
|---------|------|
|Docena|12|
|Centena|100|


## Enlances 

### Externo
- Lo genera automaticamente https://es.wikipedia.org/wiki/Wikipedia
- Si queremos hacer un hiper vinculo lo hacemos como [Wikipedia](https://es.wikipedia.org/wiki/Wikipedia)
- Para hacer esto ultimo mas rapido podemos apretar Ctrl+K y sale el formato para hacer un hiper vinculo

### Entre notas
Lo correcto seria hacer 
[MARKDOWN](MARKDOWN.md)
 donde %2F=/ y %20=Espacio en blanco

Como esto es muy dificil se usa

#### Wikilinks
donde usamor doble corchete [[MARKDOWN]]


## [[010-Areas-Fuente/Personal/Obsidian/Plantillas]]
### [[Crear tarjetas de Anki desde obsidian]]

## Ecuaciones
Se ponen entre \$\$ si se requiere colocarla en medio del texto o con \$\$\$\$ si se requiere que aparezca sola

### Potencia y Raiz
 La potencia se la coloca con ^ y la raiz con \\sqrt{algo}
 si deseamos colocar una fraccion se lo haria con \\frac{numerador}{Denominador}
 


### Letras griegas
![[Pasted image 20220722164952.png]]
$\nabla$
### Funciones

[Ecuaciones Markdown
](https://csrgxtu.github.io/2015/03/20/Writing-Mathematic-Fomulars-in-Markdown/)

