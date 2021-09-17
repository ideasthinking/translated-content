---
title: clip-path
slug: Web/CSS/clip-path
tags:
  - CSS
  - Experimental
  - Propriété
  - Reference
translation_of: Web/CSS/clip-path
---
<div>{{CSSRef}}</div>

<p>La propriété <code><strong>clip-path</strong></code> empêche une portion d'un élément d'être affichée en définissant une région de rognage. Seule une zone spécifique de l'élément sera affichée. La zone de rognage est un chemin défini avec une URL faisant référence à un SVG externe ou en ligne ou grâce à une fonction de forme comme <code><a href="/fr/docs/Web/SVG/Element/circle">circle()</a></code>.</p>

<div>{{EmbedInteractiveExample("pages/css/clip-path.html")}}</div>

<div class="note">
<p><strong>Note :</strong> La propriété <code>clip-path</code> remplace la propriété {{cssxref("clip")}} désormais dépréciée.</p>
</div>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush:css no-line-numbers">/* Valeurs avec un mot-clé */
clip-path: none;

/* Valeurs pointant vers une image */
/* Type &lt;clip-source&gt; */
clip-path: url(resources.svg#c1);

/* Valeurs de boîte */
clip-path: fill-box;
clip-path: stroke-box;
clip-path: view-box;
clip-path: margin-box;
clip-path: border-box;
clip-path: padding-box;
clip-path: content-box;

/* Valeurs géométriques            */
/* avec une notation fonctionnelle */
clip-path: inset(100px 50px);
clip-path: circle(50px at 0 100px);
clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);
clip-path: path('M0.5,1 C0.5,1,0,0.7,0,0.3 A0.25,0.25,1,1,1,0.5,0.3 A0.25,0.25,1,1,1,1,0.3 C1,0.7,0.5,1,0.5,1 Z');

/* Combinaison boîte &amp; géométrie */
clip-path: padding-box circle(50px at 0 100px);

/* Valeurs globales */
clip-path: inherit;
clip-path: initial;
clip-path: unset;
</pre>

<p>La propriété <code>clip-path</code> est définie avec une ou plusieurs des valeurs listées ci-après.</p>

<h3 id="Valeurs">Valeurs</h3>

<dl>
 <dt><code>url()</code></dt>
 <dd>Une URL qui fait référence à un élément contenant le chemin de rognage.</dd>
 <dt><code>inset()</code>, <code>circle()</code>, <code>ellipse()</code>, <code>polygon()</code></dt>
 <dd>Une fonction {{cssxref("&lt;basic-shape&gt;")}}. Une telle forme utilise la valeur <code>&lt;geometry-box&gt;</code> pour déterminer la taille et la position de la forme. Si aucune boîte de géométrie n'est indiquée, c'est la boîte de bordure (<code>border-box</code>) qui sera utilisée comme boîte de réference.</dd>
 <dt><code>&lt;geometry-box&gt;</code></dt>
 <dd>Si cette valeur est combinée avec une valeur <code>&lt;basic-shape&gt;</code>, elle définira la boîte de référence dans laquelle placer la forme. Si elle est utilisée seule, ce sont les bords de la boîte (ainsi que les éventuels coins arrondis définis avec {{cssxref("border-radius")}}) qui sont utilisés comme ligne de rognage. Cette composante peut prendre les valeurs suivante :
 <dl>
  <dt><code>fill-box</code></dt>
  <dd>La boîte englobant (<em>bounding box</em>) est utilisée comme boîte de référence.</dd>
  <dt><code>stroke-box</code></dt>
  <dd>La boîte de contour de la boîte englobante est utilisée comme boîte de référence.</dd>
  <dt><code>view-box</code></dt>
  <dd>La zone d'affichage SVG la plus proche est utilisée comme boîte de référence. Si un attribut {{SVGAttr("viewBox")}} est défini pour l'élément qui crée la zone d'affichage SVG, la boîte de référence est située à l'origine du système construit par <code>viewBox</code> et les dimensions de la boîte de référence sont les valeurs de hauteur et de largeur de l'attribut <code>viewBox</code>.</dd>
  <dt><code>margin-box</code></dt>
  <dd>La boîte de marge est utilisée comme boîte de référence</dd>
  <dt><code>border-box</code></dt>
  <dd>La boîte de bordure est utilisée comme boîte de référence</dd>
  <dt><code>padding-box</code></dt>
  <dd>La boîte de remplissage (<em>padding</em>) est utilisée comme boîte de référence</dd>
  <dt><code>content-box</code></dt>
  <dd>La boîte de contenu est utilisée comme boîte de référence.</dd>
 </dl>
 </dd>
 <dt><code>none</code></dt>
 <dd>Aucun chemin de rognage n'est créé.</dd>
</dl>

<div class="note">
<p><strong>Note :</strong> Si <a href="/fr/docs/Web/CSS/Valeur_calcul%C3%A9e">la valeur calculée</a> est différente de <code>none</code>, cela entraînera  la création d'un nouveau <a href="/fr/docs/Glossaire/Contexte_d_empilement">contexte d'empilement</a> (de la même façon qu'{{cssxref("opacity")}} avec des valeurs différentes de 1).</p>
</div>

<h3 id="Syntaxe_formelle">Syntaxe formelle</h3>

{{csssyntax}}

<h2 id="Exemples">Exemples</h2>

<h3 id="Comparaison_entre_HTML_et_SVG">Comparaison entre HTML et SVG</h3>

<pre class="brush: html hidden">&lt;svg class="defs"&gt;
  &lt;defs&gt;
    &lt;clipPath id="myPath" clipPathUnits="objectBoundingBox"&gt;
      &lt;path d="M0.5,1 C0.5,1,0,0.7,0,0.3 A0.25,0.25,1,1,1,0.5,0.3 A0.25,0.25,1,1,1,1,0.3 C1,0.7,0.5,1,0.5,1 Z" /&gt;
    &lt;/clipPath&gt;
  &lt;/defs&gt;
&lt;/svg&gt;

&lt;div class="grid"&gt;
  &lt;div class="col"&gt;
    &lt;div class="note"&gt;clip-path: none&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="none"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="none"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: url(#myPath)&lt;br&gt;&lt;br&gt;
      Assuming the following clipPath definition:
      &lt;pre&gt;
&amp;lt;svg&amp;gt;
  &amp;lt;clipPath id="myPath" clipPathUnits="objectBoundingBox"&amp;gt;
    &amp;lt;path d="M0.5,1
      C 0.5,1,0,0.7,0,0.3
      A 0.25,0.25,1,1,1,0.5,0.3
      A 0.25,0.25,1,1,1,1,0.3
      C 1,0.7,0.5,1,0.5,1 Z" /&amp;gt;
  &amp;lt;/clipPath&amp;gt;
&amp;lt;/svg&amp;gt;&lt;/pre&gt;
    &lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="svg"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="svg"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: path('M15,45 A30,30,0,0,1,75,45 A30,30,0,0,1,135,45 Q135,90,75,130 Q15,90,15,45 Z')
    &lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="svg2"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="svg2"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;



    &lt;div class="note"&gt;clip-path: circle(25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape1"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape1"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: circle(25% at 25% 25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape2"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape2"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: fill-box circle(25% at 25% 25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape3"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape3"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: stroke-box circle(25% at 25% 25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape4"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape4"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: view-box circle(25% at 25% 25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape5"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape5"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: margin-box circle(25% at 25% 25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape6"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape6"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: border-box circle(25% at 25% 25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape7"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape7"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: padding-box circle(25% at 25% 25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape8"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape8"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class="note"&gt;clip-path: content-box circle(25% at 25% 25%)&lt;/div&gt;
    &lt;div class="row"&gt;
      &lt;div class="cell"&gt; &lt;span&gt;HTML&lt;/span&gt;
        &lt;div class="container"&gt;
          &lt;p class="shape9"&gt;
            I LOVE&lt;br&gt;&lt;em&gt;clipping&lt;/em&gt;
          &lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class="cell"&gt; &lt;span&gt;SVG&lt;/span&gt;
        &lt;div class="container viewbox"&gt;
          &lt;svg viewBox="0 0 192 192"&gt;
            &lt;g class="shape9"&gt;
              &lt;rect x="24" y="24" width="144" height="144" /&gt;
              &lt;text x="96" y="91"&gt;I LOVE&lt;/text&gt;
              &lt;text x="96" y="109" class="em"&gt;clipping&lt;/text&gt;
            &lt;/g&gt;
          &lt;/svg&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;</pre>

<pre class="brush: css">html,body {
  height: 100%;
  box-sizing: border-box;
  background: #EEE;
}

.grid {
  width: 100%;
  height: 100%;
  display: flex;
  font: 1em monospace;
}

.row {
  display: flex;
  flex: 1 auto;
  flex-direction: row;
  flex-wrap: wrap;
}

.col {
  flex: 1 auto;
}

.cell {
  margin: .5em;
  padding: .5em;
  background-color: #FFF;
  overflow: hidden;
  text-align: center;
  flex: 1;
}

.note {
  background: #fff3d4;
  padding: 1em;
  margin: .5em .5em 0;
  font: .8em sans-serif;
  text-align: left;
  white-space: nowrap;
}

.note + .row .cell {
  margin-top: 0;
}

.container {
  display: inline-block;
  border: 1px dotted grey;
  position:relative;
}

.container:before {
  content: 'margin';
  position: absolute;
  top: 2px;
  left: 2px;
  font: italic .6em sans-serif;
}

.viewbox {
  box-shadow: 1rem 1rem 0 #EFEFEF inset, -1rem -1rem 0 #EFEFEF inset;
}

.container.viewbox:after {
  content: 'viewbox';
  position: absolute;
  left: 1.1rem;
  top: 1.1rem;
  font: italic .6em sans-serif;
}

.cell span {
  display: block;
  margin-bottom: .5em;
}

p {
  font-family: sans-serif;
  background: #000;
  color: pink;
  margin: 2em;
  padding: 3em 1em;
  border: 1em solid pink;
  width: 6em;
}

.none { clip-path: none; }
.svg  { clip-path: url(#myPath); }
.svg2 { clip-path: path('M15,45 A30,30,0,0,1,75,45 A30,30,0,0,1,135,45 Q135,90,75,130 Q15,90,15,45 Z');}
.shape1 { clip-path: circle(25%); }
.shape2 { clip-path: circle(25% at 25% 25%); }
.shape3 { clip-path: fill-box    circle(25% at 25% 25%); }
.shape4 { clip-path: stroke-box  circle(25% at 25% 25%); }
.shape5 { clip-path: view-box    circle(25% at 25% 25%); }
.shape6 { clip-path: margin-box  circle(25% at 25% 25%); }
.shape7 { clip-path: border-box  circle(25% at 25% 25%); }
.shape8 { clip-path: padding-box circle(25% at 25% 25%); }
.shape9 { clip-path: content-box circle(25% at 25% 25%); }

.defs {
  width: 0;
  height: 0;
  margin: 0;
}

pre { margin-bottom: 0; }

svg {
  margin: 1em;
  font-family: sans-serif;
  width: 192px;
  height: 192px;
}

svg rect {
  stroke: pink;
  stroke-width: 16px;
}

svg text {
  fill: pink;
  text-anchor: middle;
}

svg text.em {
  font-style: italic;
}</pre>

<p>{{EmbedLiveSample("Comparaison_entre_HTML_et_SVG", "100%", 800, "", "", "example-outcome-frame")}}</p>

<h3 id="Exemple_complet">Exemple complet</h3>

<h4 id="HTML">HTML</h4>

<pre class="brush: html">&lt;img id="clipped" src="https://mdn.mozillademos.org/files/12668/MDN.svg"
    alt="MDN logo"&gt;
&lt;svg height="0" width="0"&gt;
  &lt;defs&gt;
    &lt;clipPath id="cross"&gt;
      &lt;rect y="110" x="137" width="90" height="90"/&gt;
      &lt;rect x="0" y="110" width="90" height="90"/&gt;
      &lt;rect x="137" y="0" width="90" height="90"/&gt;
      &lt;rect x="0" y="0" width="90" height="90"/&gt;
    &lt;/clipPath&gt;
  &lt;/defs&gt;
&lt;/svg&gt;

&lt;select id="clipPath"&gt;
  &lt;option value="none"&gt;none&lt;/option&gt;
  &lt;option value="circle(100px at 110px 100px)"&gt;circle&lt;/option&gt;
  &lt;option value="url(#cross)" selected&gt;cross&lt;/option&gt;
  &lt;option value="inset(20px round 20px)"&gt;inset&lt;/option&gt;
  &lt;option value="path('M 0 200 L 0,110 A 110,90 0,0,1 240,100 L 200 340 z')"&gt;path&lt;/option&gt;
&lt;/select&gt;
</pre>

<h4 id="CSS">CSS</h4>

<pre class="brush: css">#clipped {
  margin-bottom: 20px;
  clip-path: url(#cross);
}
</pre>

<pre class="brush: js hidden">var clipPathSelect = document.getElementById("clipPath");
clipPathSelect.addEventListener("change", function (evt) {
  document.getElementById("clipped").style.clipPath = evt.target.value;
});
</pre>

<h4 id="Résultat">Résultat</h4>

<p>{{EmbedLiveSample("Exemple_complet", 230, 250)}}</p>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">État</th>
   <th scope="col">Commentaires</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName("CSS Masks", "#the-clip-path", 'clip-path')}}</td>
   <td>{{Spec2('CSS Masks')}}</td>
   <td>Extension aux élément HTML. <code>clip-path</code> remplace la propriété {{cssxref("clip")}} désormais dépréciée.</td>
  </tr>
  <tr>
   <td>{{SpecName('SVG1.1', 'masking.html#ClipPathProperty', 'clip-path')}}</td>
   <td>{{Spec2('SVG1.1')}}</td>
   <td>Définition initiale (s'applique uniquement aux éléments SVG)</td>
  </tr>
 </tbody>
</table>

<p>{{cssinfo}}</p>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("css.properties.clip-path")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{cssxref("mask")}}</li>
 <li>{{cssxref("filter")}}</li>
 <li><a href="/fr/docs/Applying_SVG_effects_to_HTML_content">Appliquer des effets SVG sur du contenu HTML</a></li>
 <li><a href="https://hacks.mozilla.org/2017/06/css-shapes-clipping-and-masking/">Les formes CSS, le <em>clipping</em> et le <em>masking</em> : comment les utiliser (article en anglais)</a></li>
 <li>L'attribut SVG {{SVGAttr("clip-path")}}</li>
 <li>L'attribut SVG {{SVGAttr("clip-rule")}}</li>
</ul>