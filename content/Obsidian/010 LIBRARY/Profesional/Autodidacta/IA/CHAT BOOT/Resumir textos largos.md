## Resumen sobre Cómo Resumir Textos con ChatGPT

### Limitaciones del Resumen Automático

- El resumen generado carece de coherencia al centrarse en mencionar referencias sin explicar su relevancia.
- Ausencia de explicación sobre la razón de incluir ciertos conceptos y referencias en el resumen final.
- El enfoque del resumen automático se centra en listar los elementos utilizados en el artículo sin destacar la contribución del autor ni elaborar opiniones.

### Recomendaciones para el Uso Efectivo

- El método es más adecuado para resumir artículos altamente informativos y estructurados.
- No es eficiente para resumir opiniones o ensayos, ya que no articula ni elabora sobre las referencias mencionadas.
- Se sugieren dos recursos adicionales para mejorar el uso del método: la función Custom Instructions y una extensión para Chrome.

## Prompt

### En ingles

Article: {Insertar artículo}

You will generate increasingly concise entity-dense summaries of the above article, summarize always in the same language the article is originally written. So, the first thing you have to do is determine the language to continue all the processes in that language.

Once written your first summary in the same language as the original article, repeat the following 2 steps 5 times.

Step 1: Identify 1-3 informative entities (delimited) from the article which are missing from the previously generated summary.  
Step 2: Write a new denser summary of identical length which covers every entity and detail from the previous summary plus the missing entities.  
A missing entity is:

Relevant: to the main stories.  
Specific: descriptive yet concise (5 words or fewer).  
Novel: not in the previous summary.  
Faithful: present in the article.  
Anywhere: located in the article.

For every step, list by order of relevance all the entities that must be included until this step.

Guidelines:  
The first summary should be long (4-5 sentences, ~80 words), yet highly non-specific, containing little information beyond the entities marked as missing. Use overly verbose language and fillers (e.g., “this article discusses”) to reach ~80 words.  
Make every word count. Rewrite the previous summary to improve flow and make space for additional entities.  
Make space with fusion, compression, and removal of uninformative phrases like “the article discusses”.  
The summaries should become highly dense and concise, yet self-contained, e.g., easily understood without the article.  
Missing entities can appear anywhere in the new summary.  
Never drop entities from the previous summary. If space cannot be made, add fewer new entities. Write the summary prioritizing the order of importance of the entities.  
Remember: Use the exact same number of words for each summary.

At the end of your last summary analyze it and the list of entities mentioned and suggest how you would improve it by discarding least relevant entities or adding missing entities.


### Español
Artículo: {Insertar artículo}

Generará resúmenes cada vez más concisos y densos en entidades del artículo anterior, resumiendo siempre en el mismo idioma en el que se escribió originalmente el artículo. Entonces, lo primero que tienes que hacer es determinar el idioma para continuar todos los procesos en ese idioma.

Una vez escrito tu primer resumen en el mismo idioma que el artículo original, repite los siguientes 2 pasos 5 veces.

Paso 1: Identifique 1-3 entidades informativas (delimitadas) del artículo que faltan en el resumen generado previamente.
Paso 2: escriba un nuevo resumen más denso de idéntica longitud que cubra cada entidad y detalle del resumen anterior más las entidades que faltan.
Una entidad faltante es:

Relevante: para las historias principales.
Específico: descriptivo pero conciso (5 palabras o menos).
Novela: no en el resumen anterior.
Fiel: presente en el artículo.
En cualquier lugar: ubicado en el artículo.

Para cada paso, enumere por orden de relevancia todas las entidades que deben incluirse hasta este paso.

Pautas:
El primer resumen debe ser largo (4-5 oraciones, ~80 palabras), pero muy poco específico y contener poca información más allá de las entidades marcadas como faltantes. Utilice lenguaje demasiado detallado y rellenos (por ejemplo, “este artículo analiza”) para llegar a ~80 palabras.
Haz que cada palabra cuente. Vuelva a escribir el resumen anterior para mejorar el flujo y dejar espacio para entidades adicionales.
Haga espacio fusionando, comprimiendo y eliminando frases poco informativas como “el artículo analiza”.
Los resúmenes deben ser muy densos y concisos, pero al mismo tiempo autónomos, es decir, fáciles de entender sin el artículo.
Las entidades faltantes pueden aparecer en cualquier parte del nuevo resumen.
Nunca elimine entidades del resumen anterior. Si no se puede hacer espacio, agregue menos entidades nuevas. Redactar el resumen priorizando el orden de importancia de las entidades.
Recuerde: utilice exactamente la misma cantidad de palabras para cada resumen.

Al final de su último resumen, analícelo junto con la lista de entidades mencionadas y sugiera cómo mejorarlo descartando entidades menos relevantes o agregando entidades faltantes.