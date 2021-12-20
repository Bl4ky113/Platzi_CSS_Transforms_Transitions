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



