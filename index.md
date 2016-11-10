---
title       : Investigación Reproducible 
subtitle    : Conceptos e Ideas 
author      : Kevin Pérez C, profesor auxiliar 
job         : Departamento de Matemáticas y Estadística - Universidad de Córdoba
logo        : unicordoba3.png
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [bootstrap, quiz, shiny, interactive, mathjax]
mode        : selfcontained 
ext_widgets: {rCharts: [libraries/nvd3]}
knit        : slidify::knit2slides
---

## Replicación

- La norma estándar para reforzar la evidencia científica es la replicación de
conclusiones y la realización de estudios con independientes actores 

   + Investigadores 
   + Datos 
   + Métodos analíticos 
   + Laboratorios 
   + Instrumentos 
    
- La replicación es particularmente importante en estudios de gran impacto social y de generación de políticas publicas 

---

## Que pasa con la replicación?

- Algunos estudios no pueden ser replicados 

   + Por tiempo
   + Dinero 
   + Únicos 

- **_Investigacion reproducible_**: Hacer que los datos analíticos y el código estén disponibles para que otros puedan reproducir los resultados

---

## Como podemos cubrir la brecha ?

<center> <img src="./assets/img/img1.png"  /> </center>

---


##  Como podemos cubrir la brecha ?

<center> <img src="./assets/img/img2.png"  /> </center>

---

## Por que necesitamos la investigación reproducible?


- Las nuevas tecnologías aumentan el rendimiento de la recopilación de datos; los datos son cada vez más complejos y de dimensiones extremadamente grandes.

- Las bases de datos existente se pueden fusionar para crear "mega bases de datos"

- El poder computacional ha aumentado considerablemente, permitiendo análisis mucho mas sofisticados 

- Por cada campo "$X$", existe un campo "$X$ Computacional"  

---

## Ruta de la investigación 

<center> <img src="./assets/img/img3.png"  height="450" /> </center>

---

## Ruta de la investigación 

<center> <img src="./assets/img/img4.png"  height="450" /> </center>

---

## Recientes desarrollos 

<center> <img src="./assets/img/img5.png"  height="450" /> </center>

---

## Noticias  

<center> <img src="./assets/img/img6.png"  height="450" /> </center>

---

## Que se necesita?

- Análisis de datos este disponible 
- Código analítico este disponible 
- Documentación de código y datos 
- Medios de distribución estándar

---


## Quienes son los actores?

- Autores 
   + Quieren que sus investigaciones sean reproducibles 
   + Quieren herramientas para la "IR", hacer su trabajo más fácil 

- Lectores 
   + Quieren reproducir resultados interesantes 
   + Quieren herramientas para "IR", hacer su trabajo fácil 

---


## Retos 

- Los autores deben hacer esfuerzos considerables para poner datos y/o resultados en la web 

- Los lectores deben descargar esa información de la web individualmente y ponerlos juntos

- Los lectores quizá no tengan los mismos recursos que los autores 

- Solo unas pocas herramientas ayudan a estas tareas para autores y lectores

---


## En la realidad ...

- Autores 
   + Solo suben material a la web 
   + Existen algunas bases de datos para varios campos 
   
- Lectores 
   + Solo descargan datos y tratan de deducir 
   + Juntan piezas de códigos y corren para ver que sucede 

---


## Literate (Statistical) Programing

- Un articulo es un flujo de **texto** y **código** 
- El análisis del código es dividido entre texto y "_chunks_" de códigos
- Cada "_chunks_" carga datos y calcula resultados
- Los resultados tiene distintos formatos de presentación (Tablas, figuras, etc.)
- El texto del articulo explica que esta sucediendo 
- Los _Literate programs_ pueden ser concebidos para producir documentos legibles para humanos y embebidos para ser computacionalmente legibles. 

---

## Literate (Statistical) Programing

- _Literate statistical programing_ es en general un concepto que requiere 
   + Un lenguaje de documentación (legible para humanos)
   + Un lenguaje de programación (legible para maquinas)
- `Sweave` utiliza $\LaTeX$ y $R$ como lenguajes de documentación y programación 
- `Sweave` fue desarrollado por _Friedrich Leisch_ (miembro del R core) 

---

## Limitaciones de `Sweave`

- `Sweave` tiene muchas limitaciones 
- Se centra principalmente en el uso de $\LaTeX$ 
- Le faltan ciertas características como capturas, gráficos múltiples por "chunks", mezcla de lenguajes de programación y muchos otros items técnicos
- No es actualizado con frecuencia

---

## Literate (Statistical) Programing

- `knitr` es un paquete escrito en $R$ surge como una alternativa 
- Reúne muchas características para abordar las limitaciones de `Sweave` 
- `knitr` usa principalmente $R$ como lenguaje de programación y una variedad de lenguajes de documentación 
   + `HTML`, `Markdown`, $\LaTeX$
- `knitr` fue desarrollado por _Yihui Xie_ (Estudiante de posgrado en _Iowa State_)

--- 

## Códigos y gráficos 


```r
require(rCharts)
haireye = as.data.frame(HairEyeColor)
n1 <- nPlot(Freq ~ Hair, group = 'Eye', type = 'multiBarChart', 
            data = subset(haireye, Sex == 'Male')) ; n1$print('chart1')
```


<div id = 'chart1' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart1()
    });
    function drawchart1(){  
      var opts = {
 "dom": "chart1",
"width":    800,
"height":    400,
"x": "Hair",
"y": "Freq",
"group": "Eye",
"type": "multiBarChart",
"id": "chart1" 
},
        data = [
 {
 "Hair": "Black",
"Eye": "Brown",
"Sex": "Male",
"Freq":             32 
},
{
 "Hair": "Brown",
"Eye": "Brown",
"Sex": "Male",
"Freq":             53 
},
{
 "Hair": "Red",
"Eye": "Brown",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Blond",
"Eye": "Brown",
"Sex": "Male",
"Freq":              3 
},
{
 "Hair": "Black",
"Eye": "Blue",
"Sex": "Male",
"Freq":             11 
},
{
 "Hair": "Brown",
"Eye": "Blue",
"Sex": "Male",
"Freq":             50 
},
{
 "Hair": "Red",
"Eye": "Blue",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Blond",
"Eye": "Blue",
"Sex": "Male",
"Freq":             30 
},
{
 "Hair": "Black",
"Eye": "Hazel",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Brown",
"Eye": "Hazel",
"Sex": "Male",
"Freq":             25 
},
{
 "Hair": "Red",
"Eye": "Hazel",
"Sex": "Male",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Hazel",
"Sex": "Male",
"Freq":              5 
},
{
 "Hair": "Black",
"Eye": "Green",
"Sex": "Male",
"Freq":              3 
},
{
 "Hair": "Brown",
"Eye": "Green",
"Sex": "Male",
"Freq":             15 
},
{
 "Hair": "Red",
"Eye": "Green",
"Sex": "Male",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Green",
"Sex": "Male",
"Freq":              8 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus" || opts.type==="bulletChart")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .width(opts.width)
          .height(opts.height)
          
        if (opts.type != "bulletChart"){
          chart
            .x(function(d) { return d[opts.x] })
            .y(function(d) { return d[opts.y] })
        }
          
         
        
          
        

        
        
        
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>

--- 

## Formulas y gráficos 

$$
    \begin{equation}
f(x) = \frac{1}{\sqrt{2\pi\sigma^2}}e^{-(x-\mu)^2/2\sigma^2}
\end{equation}
$$


<img src="assets/fig/unnamed-chunk-2-1.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" style="display: block; margin: auto;" />

---
