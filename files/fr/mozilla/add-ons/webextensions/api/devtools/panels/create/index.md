---
title: devtools.panels.create()
slug: Mozilla/Add-ons/WebExtensions/API/devtools/panels/create
tags:
  - API
  - Add-ons
  - Create
  - Extensions
  - Reference
  - WebExtensions
  - devtools.panels
translation_of: Mozilla/Add-ons/WebExtensions/API/devtools.panels/create
original_slug: Mozilla/Add-ons/WebExtensions/API/devtools.panels/create
---
<div>{{AddonSidebar()}}</div>

<p>Ajoute un nouveau panneau aux devtools.</p>

<p>Cette fonction prend : un titre, une URL vers un fichier d'icône et une URL vers un fichier HTML. Il crée un nouveau panneau dans les devtools, dont le contenu est spécifié par le fichier HTML. Il renvoie une <code><a href="/fr/docs/Web/JavaScript/Reference/Objets_globaux/Promise">Promise</a></code> qui résout un objet <code><a href="/fr/Add-ons/WebExtensions/API/devtools.panels/ExtensionPanel">ExtensionPanel</a></code> représentant le nouveau panneau.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">var creating = browser.devtools.panels.create(
  title,       // string
  iconPath,    // string
  pagePath     // string
)
</pre>

<h3 id="Parametères">Parametères</h3>

<dl>
 <dt><code>title</code></dt>
 <dd><code>string</code>. Le titre du panneau. Cela apparaitra dans la rangée des onglets le long du haut de la fenêtre des devtools, et c'est la principale façon dont l'utilisateur pourra identifier votre panneau.</dd>
 <dt><code>iconPath</code></dt>
 <dd><code>string</code>. Spécifie une icône qui sera affichée à côté du titre. Il est fourni sous forme d'URL vers un fichier image qui a été fourni avec votre extension. L'URL est résolue par rapport à la page d'extension courante (sauf si elle est exprimée en url absolue, par exemple "/icons/panel.png").</dd>
 <dt><code>pagePath</code></dt>
 <dd>string. Spécifie un fichier HTML qui définit le contenu réel du panneau. Il est fourni sous la forme d'une URL d'un fichier HTML qui a été regroupé avec votre extension. L'URL est résolue par rapport à la page d'extension courante (sauf si elle est exprimée en url absolue, par exemple "/devtools/panel.html"). Le fichier HTML peut include des fichiers CSS et JavaScript, juste comme une page web normale. Le JavaScript en cours d'éxécution dans le panneau pourra utiliser les API devtools. Voir <a href="/fr/docs/Mozilla/Add-ons/WebExtensions/Extending_the_developer_tools">Extention des outils de développement</a>.</dd>
</dl>

<h3 id="Valeur_retournée">Valeur retournée</h3>

<p>Une <code><a href="/fr/docs/Web/JavaScript/Reference/Objets_globaux/Promise">Promise</a></code> qui sera remplie avec un objet <code><a href="/fr/Add-ons/WebExtensions/API/devtools.panels/ExtensionPanel">ExtensionPanel</a></code> représentant le nouveau panneau.</p>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.api.devtools.panels.create")}}</p>

<h2 id="Exemples">Exemples</h2>

<p>Créer un nouveau panneau, et ajoute des auditeurs à ces événements onShown et  onHidden :</p>

<pre class="brush: js">function handleShown() {
  console.log("panel is being shown");
}

function handleHidden() {
  console.log("panel is being hidden");
}

browser.devtools.panels.create(
  "My Panel",                 // title
  "/icons/star.png",           // icon
  "/devtools/panel/panel.html" // content
).then((newPanel) =&gt; {
  newPanel.onShown.addListener(handleShown);
  newPanel.onHidden.addListener(handleHidden);
});
</pre>

<p>{{WebExtExamples}}</p>

<div class="note"><p><strong>Note :</strong></p>

<p>Cette API est basée sur l'API Chromium <a href="https://developer.chrome.com/extensions/devtools_panels"><code>chrome.devtools.panels</code></a>.</p>

<p>Les données de compatibilité relatives à Microsoft Edge sont fournies par Microsoft Corporation et incluses ici sous la licence Creative Commons Attribution 3.0 pour les États-Unis.</p>
</div>

<div class="hidden">
<pre>// Copyright 2015 The Chromium Authors. All rights reserved.
//
// Redistribution and use in source and binary forms, with or without
// modification, are permitted provided that the following conditions are
// met:
//
//    * Redistributions of source code must retain the above copyright
// notice, this list of conditions and the following disclaimer.
//    * Redistributions in binary form must reproduce the above
// copyright notice, this list of conditions and the following disclaimer
// in the documentation and/or other materials provided with the
// distribution.
//    * Neither the name of Google Inc. nor the names of its
// contributors may be used to endorse or promote products derived from
// this software without specific prior written permission.
//
// THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
// "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
// LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
// A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
// OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
// SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
// LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
// DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
// THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
// (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
// OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
</pre>
</div>