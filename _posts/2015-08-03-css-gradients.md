---
layout: post
title: "CSS <strong>gradients</strong>"
subtitle: "From one color to another"
section: css
---

Cuando hablamos de degradados en CSS, hablamos de **degradados de colores**.

Hay 2 tipos de degradados en CSS:

* **lineal**: los colores van de un punto a otro, en una línea _straight_
* **radiales**: los colores van desde el centro de un círculo hasta sus bordes, en _todas_direcciones 

Un degradado se considera una **imagen de fondo** y debe utilizarse con la propiedad according.

### gradiente lineal

La sintaxis de los degradados lineales es [bastante compleja](https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient), pero la idea básica es definir:

* que **colores** que desea
* donde estos colores deben aparecer **a lo largo del eje** (al principio, medio, extremo, etc.)
* en el que **dirección** el degradado debe ir

Comencemos con un simple degradado de 2 colores:

{% highlight css %}
div{ background-image: linear-gradient(red, blue);}
{% endhighlight %}

{% highlight html %}
<div>Un simple degradado de fondo vertical</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(red, blue);">Un simple degradado de fondo vertical</div>
</div>

De forma predeterminada:

* la **dirección** es **vertical**, de _top_ a _bottom_
* el color **primero** está en el **inicio** (arriba)
* el color **segundo** está en el **final** (abajo)

#### Cambiar la dirección

Si la dirección de arriba a abajo no le conviene, puede modificarla por cualquiera de las dos:

* definiendo el **destino del degradado**, con palabras clave como `to left top`
* definiendo un **ángulo** específico en grados como `45 deg`

Esta dirección debe establecerse _antes_ los colores:

{% highlight css %}
div{ background-image: linear-gradient(to bottom right, yellow, purple); width: 200px;}
{% endhighlight %}

{% highlight html %}
<div>Un degradado diagonal desde la esquina superior izquierda hasta la parte inferior derecha</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(to bottom right, yellow, purple); width: 200px;">Un degradado diagonal desde la esquina superior izquierda hasta la parte inferior derecha</div>
</div>

Si desea un ángulo más **específico**, puede utilizar un valor en **grados**:

* `0deg` es el valor predeterminado, de arriba a abajo
* `20deg` es ligeramente diagonal, va **en el sentido de las agujas del reloj**
* `90deg` es como las 15:00, de derecha a izquierda
* `180deg` es de abajo a arriba

{% highlight css %}
div{ background-image: linear-gradient(20deg, green, blue); width: 150px;}
{% endhighlight %}

{% highlight html %}
<div>Un gradiente diagonal con un ángulo de 20 grados</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(20deg, green, blue); width: 150px;">Un gradiente diagonal con un ángulo de 20 grados</div>
</div>

#### Adición de más colores

Puede insertar tantos colores como desee. Se distribuirán **igualmente** a lo largo del eje:

* **2 colores**: 0% y 100%
* **3 colores**: 0%, 50% y 100%
* **4 colores**: 0%, 33%, 67% y 100%

{% highlight css %}
div{ background-image: linear-gradient(orange, grey, yellow); width: 150px;}
{% endhighlight %}

{% highlight html %}
<div>Un gradiente bastante feo, pero tienes la idea</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(orange, grey, yellow); width: 150px;">Un gradiente bastante feo, pero tienes la idea</div>
</div>

#### Configuración de paradas de color específicas

Si no desea que los colores se distribuyan por igual, puede establecer posiciones de parada de color específicas**, utilizando cualquiera de los porcentajes `%` o pixels `px`:

{% highlight css %}
div{ background-image: linear-gradient(orange, grey 10%, yellow 50%); width: 150px;}
{% endhighlight %}

{% highlight html %}
<div>Un gradiente aún más feo, pero tienes la idea</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(orange, grey 10%, yellow 50%); width: 150px;">Un gradiente aún más feo, pero tienes la idea</div>
</div>

En esta configuración:

* `orange` no tiene ninguna posición de parada, por lo que por defecto a **cero** `0%`
* `grey` está más cerca de la parte superior, en `10%` instead of `50%`
* `yellow` toma la mitad del gradiente, de `50%` hasta el final `100%`

### gradiente radial

Mientras que los degradados lineales siguen un eje de una sola línea, **degradados radiales** se extienden en todas las direcciones. Su sintaxis es bastante similar a las lineales, ya que ambas tienen paradas de color **. Pero en lugar de especificar un _direction_ debe especificar:

* una **shape**: ya sea un círculo o una elipse
* un **punto de partida**: que será el centro del círculo/elipse
* un **punto final**: donde el borde del círculo / elipse será

{% highlight css %}
div{ background-image: radial-gradient(red, yellow); padding: 1rem; width: 300px;}
{% endhighlight %}

{% highlight html %}
<div>Esto parece el sol, ¿no?e</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: radial-gradient(red, yellow); padding: 1rem; width: 300px;">Esto parece el sol, ¿no?e</div>
</div>

De forma predeterminada:

* el degradado es una **elipse**
* el primer color comienza en el **center**
* el último color termina en la esquina **más lejana**

#### posición de inicio

La posición **start** funciona como **[posiciones de fondo](/css-background.html#background-position)**. You set it with the `at` keyword.

{% highlight css %}
div{ background-image: radial-gradient(at top right, black, lightgrey); padding: 1rem; width: 300px;}
{% endhighlight %}

{% highlight html %}
<div>A gloomy day.</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: radial-gradient(at top right, black, lightgrey); padding: 1rem; width: 300px;">A gloomy day.</div>
</div>

#### end position

By default, the shape will end at the **farthest corner**. You can either choose:

* `closest-side`
* `closest-corner`
* `farthest-side`
* `farthest-corner`

The difference is both hard to grasp and to visualize, so I won't go into details. Mozilla has a [good description of the different values](https://developer.mozilla.org/en-US/docs/Web/CSS/radial-gradient#Values).

{% highlight css %}
div{ background-image: radial-gradient(closest-corner at 20px 20px, green, blue); padding: 1rem; width: 300px;}
div:hover{ background-image: radial-gradient(farthest-side at 20px 20px, green, blue)}
{% endhighlight %}

{% highlight html %}
<div>Hover this green star in the sky to see it expand.</div>
{% endhighlight %}

<div class="result" id="result-831">
  <div>Hover this green star in the sky to see it expand.</div>
</div>

#### fixed size

Instead of setting both start _and_ end positions, you can just set **specific dimensions**:

{% highlight css %}
div{ background-image: radial-gradient(20px 10px at 75% 50%, darkviolet, pink); padding: 1rem; width: 300px;}
{% endhighlight %}

{% highlight html %}
<div>A small violet disc in a sea of pink.</div>
{% endhighlight %}

<div class="result">
  <div style="background-image: radial-gradient(20px 10px at 75% 50%, darkviolet, pink); padding: 1rem; width: 300px;">A small violet disc in a sea of pink.</div>
</div>

CSS gradients are powerful, considering how endless the options are.

The examples of this page are voluntarily "ugly", with pronounced color differences, to better explain what how each property works.

But it's quite easy to write more **subtle** gradients, especially for buttons:

{% highlight css %}
.button-grey  { background-image: linear-gradient(#f2f2f2, #f2f2f2);}
.button-yellow{ background-image: linear-gradient(#fce374, #fcdf5b);}
.button-orange{ background-image: linear-gradient(#f58a38, #f57c20);}
.button-red   { background-image: linear-gradient(#ed6d64, #ed574c);}
.button-purple{ background-image: linear-gradient(#847bba, #7568ba);}
.button-blue  { background-image: linear-gradient(#42b0e3, #2ba9e3);}
.button-green { background-image: linear-gradient(#97cc76, #8bcc62);}
{% endhighlight %}

<div class="result" id="result-832">
  <a class="button-grey">Button</a>
  <a class="button-yellow">Button</a>
  <a class="button-orange">Button</a>
  <a class="button-red">Button</a>
  <a class="button-purple">Button</a>
  <a class="button-blue">Button</a>
  <a class="button-green">Button</a>
</div>

<style type="text/css">
#result-831{ padding: 1rem;}
#result-831 div{ background-image: radial-gradient(closest-corner at 20px 20px, green, blue); padding: 1rem; width: 300px;}
#result-831 div:hover{ background-image: radial-gradient(farthest-side at 20px 20px, green, blue)}
#result-832{ padding: 1rem;}
#result-832 a{ background-image: linear-gradient(lightblue, skyblue); border: 1px solid #eee; border-radius: 3px; color: grey; display: inline-block; line-height: 32px; padding: 0 15px; text-decoration: none; transition: none; vertical-align: top;}
#result-832 .button-grey {
  background-color: #f2f2f2;
  background-image: linear-gradient(to bottom, #f2f2f2, #f2f2f2);
  border: 1px solid #bfbfbf;
  box-shadow: inset 0 1px 0 white, inset 0 -1px 0 #d9d9d9, inset 0 0 0 1px #f2f2f2, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: #8c8c8c;
  text-shadow: 0 1px 0 rgba(255, 255, 255, 0.5);
}
#result-832 .button-grey:hover, #result-832 .button-grey:focus {
  background: #f2f2f2;
  border-color: #8c8c8c;
  box-shadow: inset 0 1px 0 white, inset 0 -1px 0 #d9d9d9, inset 0 0 0 1px #f2f2f2;
}
#result-832 .button-grey:active {
  background: #f2f2f2;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-blue {
  background-color: #42b0e3;
  background-image: linear-gradient(to bottom, #42b0e3, #2ba9e3);
  border: 1px solid #107db0;
  box-shadow: inset 0 1px 0 #7cd4fc, inset 0 -1px 0 #2696c9, inset 0 0 0 1px #59b7e3, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-blue:hover, #result-832 .button-blue:focus {
  background: #2ba9e3;
  border-color: #004c6f;
  box-shadow: inset 0 1px 0 #7cd4fc, inset 0 -1px 0 #2696c9, inset 0 0 0 1px #59b7e3;
}
#result-832 .button-blue:active {
  background: #2ba9e3;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-green {
  background-color: #97cc76;
  background-image: linear-gradient(to bottom, #97cc76, #8bcc62);
  border: 1px solid #5f993a;
  box-shadow: inset 0 1px 0 #c6e5b3, inset 0 -1px 0 #79b356, inset 0 0 0 1px #a4cc8b, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-green:hover, #result-832 .button-green:focus {
  background: #8bcc62;
  border-color: #326612;
  box-shadow: inset 0 1px 0 #c6e5b3, inset 0 -1px 0 #79b356, inset 0 0 0 1px #a4cc8b;
}
#result-832 .button-green:active {
  background: #8bcc62;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-purple {
  background-color: #847bba;
  background-image: linear-gradient(to bottom, #847bba, #7568ba);
  border: 1px solid #493e87;
  box-shadow: inset 0 1px 0 #bab6d4, inset 0 -1px 0 #655aa1, inset 0 0 0 1px #948dba, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-purple:hover, #result-832 .button-purple:focus {
  background: #7568ba;
  border-color: #1f1654;
  box-shadow: inset 0 1px 0 #bab6d4, inset 0 -1px 0 #655aa1, inset 0 0 0 1px #948dba;
}
#result-832 .button-purple:active {
  background: #7568ba;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-orange {
  background-color: #f58a38;
  background-image: linear-gradient(to bottom, #f58a38, #f57c20);
  border: 1px solid #c25706;
  box-shadow: inset 0 1px 0 #ffb984, inset 0 -1px 0 #db6f1d, inset 0 0 0 1px #f59851, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-orange:hover, #result-832 .button-orange:focus {
  background: #f57c20;
  border-color: #773300;
  box-shadow: inset 0 1px 0 #ffb984, inset 0 -1px 0 #db6f1d, inset 0 0 0 1px #f59851;
}
#result-832 .button-orange:active {
  background: #f57c20;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-red {
  background-color: #ed6d64;
  background-image: linear-gradient(to bottom, #ed6d64, #ed574c);
  border: 1px solid #ba3329;
  box-shadow: inset 0 1px 0 #ffb0aa, inset 0 -1px 0 #d44d44, inset 0 0 0 1px #ed837b, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-red:hover, #result-832 .button-red:focus {
  background: #ed574c;
  border-color: #870c03;
  box-shadow: inset 0 1px 0 #ffb0aa, inset 0 -1px 0 #d44d44, inset 0 0 0 1px #ed837b;
}
#result-832 .button-red:active {
  background: #ed574c;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-yellow {
  background-color: #fce374;
  background-image: linear-gradient(to bottom, #fce374, #fcdf5b);
  border: 1px solid #c9ae34;
  box-shadow: inset 0 1px 0 #fff6ce, inset 0 -1px 0 #e3c852, inset 0 0 0 1px #fce88d, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: #967d09;
  text-shadow: 0 1px 0 rgba(255, 255, 255, 0.5);
}
#result-832 .button-yellow:hover, #result-832 .button-yellow:focus {
  background: #fcdf5b;
  border-color: #967d09;
  box-shadow: inset 0 1px 0 #fff6ce, inset 0 -1px 0 #e3c852, inset 0 0 0 1px #fce88d;
}
#result-832 .button-yellow:active {
  background: #fcdf5b;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}
</style>