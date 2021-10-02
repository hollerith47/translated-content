---
title: WheelEvent.deltaX
slug: Web/API/WheelEvent/deltaX
tags:
  - API
  - DOM
  - Lecture seulement
  - Propriété
  - Reference
  - Référence(2)
  - WheelEvent
translation_of: Web/API/WheelEvent/deltaX
---
<p>{{APIRef("DOM Events")}}</p>

<p>La propriété en lecture seule <code><strong>WheelEvent.deltaX</strong></code> est un <code>double</code> représentant la quantité de défilement horizontal dans l'unité {{domxref("WheelEvent.deltaMode")}}.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="syntaxbox">var <code><em>dX</em> = <em>event</em>.deltaX;</code></pre>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: js">var syntheticEvent = new WheelEvent("syntheticWheel", {"deltaX": 4, "deltaMode": 0});

console.log(syntheticEvent.deltaX);
</pre>

<h2 id="Spécifications">Spécifications</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Spécification</th>
   <th scope="col">Statut</th>
   <th scope="col">Commantaire</th>
  </tr>
  <tr>
   <td>{{SpecName('DOM3 Events','#widl-WheelEvent-deltaX','WheelEvent.deltaX')}}</td>
   <td>{{Spec2('DOM3 Events')}}</td>
   <td>Définiton initiale.</td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibilité_des_navigateurs">Compatibilité des navigateurs</h2>

<p>{{Compat("api.WheelEvent.deltaX")}}</p>

<h2 id="Voir_aussi">Voir aussi</h2>

<ul>
 <li>{{ event("wheel") }}</li>
 <li>{{domxref("WheelEvent")}}</li>
</ul>