---
title: name
slug: Mozilla/Add-ons/WebExtensions/manifest.json/name
tags:
  - Add-ons
  - Extensions
  - WebExtensions
translation_of: Mozilla/Add-ons/WebExtensions/manifest.json/name
---
<div>{{AddonSidebar}}</div>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row" style="width: 30%;">Type</th>
   <td>chaîne</td>
  </tr>
  <tr>
   <th scope="row">Obligatoire</th>
   <td>Oui</td>
  </tr>
  <tr>
   <th scope="row">Exemple</th>
   <td>
    <pre class="brush: json">
"name": "Mon extension"</pre>
   </td>
  </tr>
 </tbody>
</table>

<p>Nom de l'extension. Ceci permet d'identifier l'extension dans l'interface utilisateur du navigateur et sur les sites comme addons.mozilla.org.</p>

<p>Il est recommandé de garder le nom suffisamment court pour pouvoir s'afficher dans l'interface utilisateur. Google Chrome et Microsoft Edge limitent la longueur du nom à 45 caractères.</p>

<p>C'est une <a href="/fr/Add-ons/WebExtensions/Internationalization#Internationalizing_manifest.json">propriété localisable</a>.</p>

<h2 id="Exemple">Exemple</h2>

<pre class="brush: json">"name": "Mon extension"</pre>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.manifest.name")}}</p>