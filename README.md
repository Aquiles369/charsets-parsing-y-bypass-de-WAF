<h1 align="center"><img height="40" src="https://github.com/Aquiles369/iconos/blob/main/img/lobo1.gif"><img height="40" src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExNWx4YTl1dW9scXlqZDk2cTdyY2VvcXQwMG40OGoxY25rZzV0MDZhcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/peSyJWjNTRfzaWh49M/giphy.gif">"charsets, parsing y bypass de WAF."<img height="40" src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExNWx4YTl1dW9scXlqZDk2cTdyY2VvcXQwMG40OGoxY25rZzV0MDZhcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/peSyJWjNTRfzaWh49M/giphy.gif"><img height="35" src="https://github.com/Aquiles369/iconos/blob/main/img/lobo1.gif"> </h1>	


<br>


<p align="center">
 <img  height="470rem" alt="GIF" src="https://tenor.com/mvmcU2SGRyY.gif"/>
</p>

<picture> <img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">  </picture>


### <picture> <img src = "https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTJhbnhicXlyNDBiMXJ5d2JoazEyNXY3MHVqYXMyZjZ4ZTdzOWh3MCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/S4kCITUXoyg3Gyr1cN/giphy.gif" width = 75px> Normalizacion Unicode y Desalineacion entre Capas.  </picture> 

<br>

 **Catálogo técnico interactivo para analizar normalización Unicode aplicada a seguridad web. Enfocado en NFC, NFD, NFKC y NFKD y en cómo discrepancias entre WAF, backend, runtime y navegador generan desalineación semántica explotable. Incluye análisis práctico de equivalencia canónica vs compatibilidad, propiedades de Quick_Check, Composition_Exclusion y comportamiento en distintos puntos del pipeline (input → WAF → backend → runtime → navegador).** 
<br><br> 

**Proyecto en investigación activa. El contenido evoluciona conforme se validan nuevos escenarios de normalización y desalineación entre capas.** 
<br><br> 

<br>
<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExdzZhdzU1ejBxaXJhaHcwZnVqN2xxcHFhMmI2dWdudnM3ZGd3aDV1dSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/LS8dIaRdiTEFVBSxDF/giphy.gif" width = 75px>  </picture> Problema que resuelve<br><br>
**Cuando auditás aplicaciones web, muchos asumen que usar homoglyphs o caracteres “raros” es suficiente para bypass.<br><br>
El problema real es otro:<br><br>
• No todos los sistemas normalizan igual.<br><br>
• No todos normalizan en el mismo momento.<br><br>
• Algunos hacen matching antes de normalizar.<br><br>
• Otros normalizan en NFKC mientras el backend compara en NFC.</a>.** 

<br><br>

Esto genera:<br><br>

• Falsos positivos en pruebas ofensivas.<br><br>
• Payloads que “parecen funcionar” pero se recomponen y dejan de ejecutar.<br><br>
• Ventanas lógicas cuando WAF y backend interpretan distinto el mismo input.<br><br>

<br>

La superficie real no está en el carácter extraño.
Está en la desalineación semántica entre capas.

<br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>

<br>

### <picture> <img src = "https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExOXVvem9uczRjOTUycTdlM2N0a3h5Mmx1Mnl2eXg4dWg4enFya2d3NiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/WvkRfmIxMOm6iUYouv/giphy.gif" width = 75px>  </picture> Qué aporta y cómo beneficia <br><br>

<br>

• Comprensión real de NFC, NFD, NFKC y NFKD en contexto ofensivo.<br><br>
• Diferenciación técnica entre equivalencia canónica y equivalencia de compatibilidad.<br><br>
• Análisis del impacto de NFC_Quick_Check=Maybe en validaciones.<br><br>
• Estudio de Composition_Exclusion y estabilidad post Unicode 4.1.<br><br>
• Evaluación de normalización en concatenación, buffering y condiciones stream-safe.<br><br>
• Identificación de escenarios donde el orden de normalización altera el resultado final.

<br><br>

Esto permite:<br><br>

• Reducir bypass teóricos sin base técnica.<br><br>
• Detectar inconsistencias reales entre WAF y backend.<br><br>
• Enfocar pruebas en divergencias observables, no en gimmicks visuales.<br>



<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExaHR3cDVhNXY0bDZteHRkMWNrNmQzMXF4NzJ1MXoyeGU2eXMzNXA4NSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/fYMrCNMFkCeEdwB2Vo/giphy.gif" width = 80px>  </picture> Resumen rápido
<br><br>

Investigación aplicada a bug bounty ético sobre cómo la normalización Unicode puede modificar la semántica efectiva del input.<br><br>

No es un estudio de “caracteres raros”.<br><br>

Es un análisis del pipeline completo de interpretación:<br><br>

input → normalización → matching → backend → runtime → navegador<br><br>

Unicode no es solo encoding.
Es equivalencia semántica formal definida en el estándar.<br><br>

La explotación aparece cuando dos capas no aplican la misma equivalencia.<br>




<br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExaHR3cDVhNXY0bDZteHRkMWNrNmQzMXF4NzJ1MXoyeGU2eXMzNXA4NSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/fYMrCNMFkCeEdwB2Vo/giphy.gif" width = 80px>  </picture> Recursos oficiales utilizados
<br><br>


• https://www.unicode.org/versions/Unicode17.0.0/
Página oficial de versiones del estándar Unicode. Documenta reglas formales de normalización, estabilidad y definiciones normativas.<br><br>

• https://www.unicode.org/Public/UCD/latest/ucd/
Unicode Character Database (UCD). Contiene todas las propiedades formales de los codepoints: categorías, decompositions, combining classes, Quick_Check, etc. Es la base técnica real del comportamiento de normalización.<br><br>

• https://www.unicode.org/Public/UCD/latest/ucd/DerivedNormalizationProps.txt
Archivo derivado que lista propiedades específicas relacionadas con normalización, como NFC_QC, NFKC_QC y Composition_Exclusion. Fundamental para entender qué caracteres pueden cambiar bajo cada forma.<br><br>

• https://util.unicode.org/UnicodeJsps/character.jsp
Herramienta oficial para inspeccionar propiedades de un codepoint individual.<br><br>

Ejemplo:<br>
https://util.unicode.org/UnicodeJsps/character.jsp?a=2126
Permite analizar propiedades como descomposición, Quick_Check y exclusiones de composición en un carácter concreto (U+2126 OHM SIGN).<br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExNWV6Y3FmbmxpdjNwd2dhNGMydHh1OHZiZ2cxYTh6a2JxbTNoc3R1YiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/ZEl47uGZlLY3CRHl5Y/giphy.gif" width = 80px>  </picture> Enfoque
<br><br>


Investigación ofensiva con base normativa, centrada en:<br>

• Propiedades formales del estándar Unicode.<br><br>
• Divergencias reales entre motores de normalización.<br><br>
• Impacto práctico en WAF, validadores y runtimes.<br><br>
• Normalización como vector lógico, no visual.<br><br>
 
 <br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExc3YwbG9zbmU1amprdTJsbmxzYnpobzd5eGtnazB6b2FmdnllaTRhZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/h8UlsEpqiCISTKUzvz/giphy.gif" width = 80px>  </picture> “Analiza cómo NFC, NFD, NFKC y NFKD transforman realmente el input, identifica en qué punto del pipeline se normaliza y detecta desalineaciones entre WAF, backend y runtime antes de que se conviertan en superficie explotable.”
<br>


<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
