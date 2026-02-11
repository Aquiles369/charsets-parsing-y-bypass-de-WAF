<h1 align="center"><img height="40" src="https://github.com/Aquiles369/iconos/blob/main/img/lobo1.gif"><img height="40" src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExNWx4YTl1dW9scXlqZDk2cTdyY2VvcXQwMG40OGoxY25rZzV0MDZhcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/peSyJWjNTRfzaWh49M/giphy.gif">"charsets, parsing y bypass de WAF."<img height="40" src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExNWx4YTl1dW9scXlqZDk2cTdyY2VvcXQwMG40OGoxY25rZzV0MDZhcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/peSyJWjNTRfzaWh49M/giphy.gif"><img height="35" src="https://github.com/Aquiles369/iconos/blob/main/img/lobo1.gif"> </h1>	


<br>


<p align="center">
 <img  height="470rem" alt="GIF" src="https://github.com/Aquiles369/iconos/blob/main/loquillo.gif"/>
</p>

<picture> <img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">  </picture>


### <picture> <img src = "https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcDBqM3RwOWtxYjh3b2RwYml3ZWptdGxtYWRwdnRyYnkyYXQyZ3B1cSZlcD12MV9zdGlja2Vyc19zZWFyY2gmY3Q9cw/B6zEPouWkkekb8exj3/giphy.gif" width = 75px> charsets, parsing y bypass de WAF.  </picture> 

<br>

 **Investigación aplicada a seguridad web sobre cómo la negociación de charset puede alterar la interpretación real de un payload cuando distintas capas (cliente, WAF, proxy, backend, runtime) no procesan los bytes bajo la misma codificación.** <br>

Enfocado en cómo discrepancias entre Content-Type, headers HTTP, meta charset y parsers pueden generar reinterpretaciones binarias explotables.

Proyecto en investigación activa. El contenido evoluciona conforme se validan nuevos escenarios de parsing y negociación de encoding. 
 

<br>
<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExeGx6dnUxejR2Z3o1d3JncmhncTNkcGt2anJjNnJsZHc3bmw3ZTV3cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/TH2Eh9by37A2wmMHPa/giphy.gif" width = 75px>  </picture> Problema que resuelve<br><br>
**En auditorías web es común asumir que cambiar el charset siempre altera el payload.** <br><br>
El problema real es más preciso:<br><br>
• La mayoría de los entornos fuerzan UTF-8.<br><br>
• Muchos WAF inspeccionan asumiendo UTF-8 aunque el backend no lo haga.<br><br>
• Algunos proxies reescriben headers pero no el body.<br><br>
• Parsers distintos pueden interpretar los mismos bytes bajo reglas diferentes.<br><br>

En la práctica, más de 150 charsets existen formalmente (400+ alias), pero casi todo termina convergiendo en UTF-8.
La reinterpretación binaria real solo ocurre en ciertos encodings específicos.<br><br>

No distinguir esto produce:

• Pruebas inútiles sin impacto real<br><br>
• Bypass teóricos sin cambio semántico<br><br>
• Falsas conclusiones sobre evasión de WAF<br><br>

La superficie explotable no está en “cambiar charset”.
Está en cuándo y cómo se negocia la codificación entre capas.


<br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>

<br>

### <picture> <img src = "https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExYWF3ZzZ5NTlpbXA3ZHllMWc1Zjl1Yno5aWF0bXozYWpyemZ3YnVtciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/VEUoOncnj5F31yO3g3/giphy.gif" width = 75px>  </picture> Qué aporta y cómo beneficia <br><br>

<br>

• Separación técnica entre charsets meramente declarativos y aquellos con reinterpretación binaria real.<br><br>
• Análisis de inconsistencias entre meta charset y header HTTP Content-Type.<br><br>
• Estudio del comportamiento real de parsers bajo negociación de encoding.<br><br>
• Aplicación directa a XSS, filtros frágiles y WAF con inspección previa al decode.<br><br>

Encodings con potencial de reinterpretación binaria real:<br><br>

UTF-7<br><br>
UTF-16 (LE / BE)<br><br>
UTF-32 (LE / BE)<br><br>
EBCDIC legacy (cp037, cp273, cp424, cp500, cp875, cp1026, cp1140–cp1149)<br><br>

Esto permite:<br><br>

• Identificar escenarios reales de desalineación binaria.<br><br>
• Evaluar bypass de WAF basados en decode inconsistente.<br><br>
• Reducir experimentación ciega y enfocarse en divergencias verificables.



<br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media.giphy.com/media/v1.Y2lkPWVjZjA1ZTQ3czEwdWl5ODlnMmN1bHZjMHE4Y2k0ZDBicXJjcmk5MTJianRkOGNkMyZlcD12MV9zdGlja2Vyc19yZWxhdGVkJmN0PXM/9mSxIJ5qFtpv4n8DRC/giphy.gif" width = 80px>  </picture> Resumen rápido
<br><br>

Unicode domina la web y casi todo termina en UTF-8 sin reinterpretación real.<br><br>

El vector no es “usar encoding raro”.<br><br>

El vector aparece cuando dos capas no decodifican los mismos bytes bajo las mismas reglas.<br><br>

La explotación surge cuando:<br><br>

bytes → decode → matching → backend<br><br>

no siguen el mismo estándar en todas las capas.<br><br>




<br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media.giphy.com/media/v1.Y2lkPWVjZjA1ZTQ3czEwdWl5ODlnMmN1bHZjMHE4Y2k0ZDBicXJjcmk5MTJianRkOGNkMyZlcD12MV9zdGlja2Vyc19yZWxhdGVkJmN0PXM/OlASCtKlMWXXX9TYQB/giphy.gif" width = 80px>  </picture> Recursos oficiales utilizados
<br><br>


• https://www.iana.org/assignments/character-sets/character-sets.xhtml
Registro oficial de todos los charsets reconocidos y sus alias. Base normativa para identificar codificaciones válidas.<br><br>

• https://encoding.spec.whatwg.org/
Especificación oficial de cómo los navegadores modernos manejan decodificación de texto y fallback. Fundamental para entender el comportamiento real del parsing en clientes.<br><br>

• https://www.unicode.org/versions/Unicode17.0.0/
Definiciones normativas del estándar Unicode.<br><br>

• https://www.unicode.org/Public/UCD/latest/ucd/
Unicode Character Database (propiedades formales de codepoints).<br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media.giphy.com/media/v1.Y2lkPWVjZjA1ZTQ3czEwdWl5ODlnMmN1bHZjMHE4Y2k0ZDBicXJjcmk5MTJianRkOGNkMyZlcD12MV9zdGlja2Vyc19yZWxhdGVkJmN0PXM/W6i1g11QoyU6yJzln6/giphy.gif" width = 80px>  </picture> Enfoque
<br><br>


Investigación ofensiva con base normativa, centrada en:<br><br>

• Negociación real de charset en HTTP.<br><br>
• Comportamiento práctico de parsers y motores de decode.<br><br>
• Divergencias entre WAF, proxy y backend.<br><br>
• Encoding como vector lógico, no visual.<br><br>

“Analiza cómo distintos charsets transforman realmente los bytes, identifica dónde ocurre el decode en el pipeline y detecta inconsistencias entre WAF y backend antes de asumir un bypass.”
 
 <br>

<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
<br>

### <picture> <img src = "https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExc3YwbG9zbmU1amprdTJsbmxzYnpobzd5eGtnazB6b2FmdnllaTRhZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/h8UlsEpqiCISTKUzvz/giphy.gif" width = 80px>  </picture>“Examina cómo los distintos charsets reinterpretan bytes en el pipeline HTTP, identifica inconsistencias entre headers, parsers y WAF, y convierte desalineaciones de encoding en superficie explotable.”
<br>


<picture> <img src="https://user-images.githubusercontent.com/74038190/212284115-f47cd8ff-2ffb-4b04-b5bf-4d1c14c0247f.gif" width ="1050" > </picture>
