# Clase de Transitions y Transformaciones de CSS

## Porque hacer animaciones en la Web?

- Facilitar la carga cognitiva
- Facilitar la comunicación usuario - app
- Ayudan a dar la misma informacion en diferentes contextos o plataformas
- Coreografias de UI
- Llaman la atencion del usuario. En resumen todas las anteriores.

## Propiedades básicas para animar:

- tranform: nos ayuda a tranformar o cambiar el diseño de un elemento. Muy versatil.
- transition: da efectos animados a los cambios de style que tengan los elementos. 

## Pseudo Clases y Pseudo Elementos

Para realizar las transitions vamos a necesitar un trigger. Estos pueden ser hechos con JS o con el mismo 
css. Usando las pseudo clases y pseudo elementos.

### Pseudo Clases

Son estilos secundarios que puede tener un elementos. Habiendo algunos unicos cómo los de los links visitados 
o globales cómo cuando seleccionamos o pasamos por el encima el mouse a un elemento.

## Timing Functions.

Las animaciones deben tener una aceleracion, velocidad y demás cualidades fisicas al moverse. 
Para eso, existen las timing functions. Las cuales nos permite cambiar la velocidad y aceleracion 
de la animación.

## Algunas Value-Funcions de Tranform

Como sabemos con tranform podemos cambiar el diseño de un elemento, esta usa diferentes value-funciones.

- translate: es una value-function de tranform que nos permite mover el elemento en un plano, con eje X y Y.
	Aunque si es necesario se puede definir que solo actue en un eje agregandolo a el nombre de la function.
	translate(<eje X>, <eje Y>);
	translateX();
	translateY();

- rotate: nos permite rotar el elemento en grados.
	rotate(<num>deg);

- scale: nos permite agrandar o empequeñecer el tamaño del elemento por el mismo.
	scale(2) // dos veces más grande que el elemento original

- skew: nos permite deformar con angulos el elemento. 
	skew(<num>deg)

## Transform Origin

Transform origin es el punto donde se va a poder definir donde van a ocurrir las tranformaciones. 
Este se puede usar para hacer que el efecto de rotar el elemento, usando rotate(), no ocurra 
desde el centro del elemento, pero de alguna otra posición. Cómo las esquinas 
inferiores e superiores de la izquierda y la derecha. Pero si se necesita un 
punto especifico, se pueden usar valores cómo los % para determinar el eje X y Y del punto 
dentro del elemento.

transform-origin: right top;
transform-origin: 25% 75%;

## transform style y perspective

Perspective es una propiedad que nos permite darle un tipo de perspectiva a el diseño. Cómo el punto de fuga. 

Esta solo se puede usar en elementos con position relative y absolute.

Perspective (num): se tiene que usar en el elemento padre, y si se necesita, se puede cambiar el origen, para darle un efecto de mirar desde otra
perspectiva con perspective-origin. 
Despues en el elemento a el cual vamos a darle un estilo dependiendo de la perspectiva le vamos a tener que definir que se va a
trabajar en esa perspectiva usando de transform-style: preserve-3d.

Ahora cualquier transform que le hagamos, tendra en cuenta la perspectiva.

Dios me imagino haciendo un dibujo de punto de fuga. Y con Js que se pueda mover y todo.

## Backface Visibility

Es una tecnica la cual nos permite crear un tipo de carta, el cual al hacer trigger. nos revele la parte de la atras de está.

Se hace teniendo un wrapper con position relative y dos elementos con absulute. Usando transform-style: preserve-3d; para que tenga un efecto 3d
y la propiedad backface-visibility: hidden;

A los elementos vamos a darles un tranform y rotate de 180deg. En el eje X para la parte trasera y en el eje Y para la parte delantera. La primera 
se puede aplicar directamente, pero la segunda en el front, se debe aplicar con un hover, para dar el efecto de estar volteando la carta.

Se puede agregar un transition all o solo con backface-visibility para darle el efecto animado de voltear una carta.

## Parallax

Parallax es efecto visual en el cual al hacer scroll en una página web, esta va a hacer un tipo de animación o de efecto. Tiene 
que ver mucho con la perspectiva que se le puede dar a los elementos usando transform.

# Transitions

transition es una propiedad que nos va a permitir darle una animación a nuestro elemento, cuando este tenga algún cambio. Generalmente por un 
trigger.

Estas animaciones se le podran definir a algunas propiedades de CSS. Se les define el tiempo de duración de la animación, la funcion de tiempo y 
si es necesario un delay de la animación.

transition: (property) (duration) (time function) (delay);

## Time Functions

Las times functions son funciones de tiempo en las que se va a determinar el desarrollo de la animación, frente a el timepo. Animación / tiempo.
Dandole un efecto de cambios en la aceleración. Hay algunas predeterminadas que se pueden usar, pero igualmente se puede crear sus propios time 
functions.

cubic-beizer(P1, P2, P3, P4). Donde P1 y P3 estan entre 1 y 0. Hay varios convertidores en la web para hacer estas functions.

# Tips de User eXperience

## Diferentes Transitions

Para darle a nuestro elemento de vivides, si eso existe, podemos darle diferentes transitions usando el estilo del elemento, classNames extras
o triggers.

El usado es darle un transition lento en el elemento y otro rapido en un trigger. Haciendo que cuando se active se mueva rapido, pero lento al 
devolverse.

## Tiempos de Expera

Algunas veces al tener elementos cómo un nav. La opciones internas de una opción, al mover el mouse fuera del elemento, se desaparecen. 
Causando frustación y perdida de tiempo. Para evitar esto deberiamos agregar y arreglarlo usando transitions en la visibilidad del objeto, usando 
propiedades cómo opacity, visibility y en casos extremos display.

## Parpadeo en la animaciones

En todo el curso hemos visto que al hacer un trigger, generalmente hover, las animaciones se empezaban a iniciar y terminar erraticamente. 
No sé porque ocurren, pero hasta a la profe le ocurria el problema en la clase. 

La forma de solucionarlo es simple, solo debemos poner un wrapper para el elemento y dejarle el trigger a este y no a el elemento. Ya que 
como el wrapper va a estar quieto sin animación, translate o transition. No le va a afectar el parpadeo o movimiento erratico.

# Propiedades cuales animar y cuales no.

En el procesamiento de una página web, se debe aplicar el style, esto en páginas estaticas cómo wikipedia ocurre generalmente solo en el inicio.
En elementos con triggers cómo hover ocurre cuando este ocurriendo. Y cuando hacemos algo animado o con transiciones, se aplica cada frame de esta.

Cada propiedad no es igual en el momento de aplicar el style. Por eso se tiene 3 categorias de propiedades dependiendo de cómo afectan el 
procesamiento de una página web.

El procesamiento de la página es el siguiente:

JS > Style > Layout > Paint > Composite

Este es realizado cada vez que se aplica un cambio visual, en el JS o en general la página.

Los cambios por parte de CSS & más especifico las animaciones y transiciones son en: Layout > Paint > Composite.

Las propiedades que NO debemos animar o transicionar son aquellas que tienen paso o procesamiento de Layout. Cambios a el Box Layout o el Layout en general.
Algunas que no son recomendadas son las que tienen procesamiento en Paint. Cambios a colores.
Y las que deberiamos cambiar son las que tienen procesamiento en Composite. Esto es así porque al procesar la propiedad, debe procesarse tambien en todos los procesamientos siguientes.

Hay muy pocas que solo tengan efecto en Composite, aunque si deberiamos evitar a todas las demas de darles un uso intensivo.

Una de las propiedades con menor peso es Transform, haciendolo mejor candidato para ser usado, por ejemplo para mover algo, con translate() que 
left, top, bottom u right.

# Rendimiento Y Accesibilidad

## Will Change

Will Change es una propiedad que nos permite resistir un poco la explicación de ariba, haciendo que las propiedades que se procesen en Layout
cogan un poco más de recursos, pero que tengan mayor rendimiento. 

En esta solo debemos definir las propiedades que necesiten mayor número de recursos.

## Movimiento Reducido

En algunos casos se necesita de movimiento reducido en las animaciones para mayor accesibilidad. La forma de poder cambiar frente a esta 
opción nuestro style es usar el media Query de: prefers-reduced-motion: reduce.

# Fin Del Curso

