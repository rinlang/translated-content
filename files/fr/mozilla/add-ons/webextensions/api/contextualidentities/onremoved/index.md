---
title: contextualIdentities.onRemoved
slug: Mozilla/Add-ons/WebExtensions/API/contextualIdentities/onRemoved
tags:
  - API
  - Add-ons
  - Event
  - Extensions
  - Reference
  - WebExtensions
  - contextualIdentities
  - onRemoved
translation_of: Mozilla/Add-ons/WebExtensions/API/contextualIdentities/onRemoved
---
<div>{{AddonSidebar()}}</div>

<p>Lancé lorsqu'une nouvelle identité contextuelle est supprimée. Les identités contextuelles peuvent être supprimées par des extensions en utilisant l'API <code>contextualIdentities</code>,  ou directement par l'utilisateur, en utilisant l'interface utilisateur du navigateur.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">browser.contextualIdentities.onRemoved.addListener(listener)
browser.contextualIdentities.onRemoved.removeListener(listener)
browser.contextualIdentities.onRemoved.hasListener(listener)
</pre>

<p>Les événements ont trois fonctions :</p>

<dl>
 <dt><code>addListener(listener)</code></dt>
 <dd>Ajoute un écouteur à cet événement.</dd>
 <dt><code>removeListener(listener)</code></dt>
 <dd>Arrêtez d'écouter cet événement. L'argument <code>listener</code> est l'écouteur à supprimer.</dd>
 <dt><code>hasListener(listener)</code></dt>
 <dd>Vérifiez si <code>listener</code> est enregistré pour cet événement. Renvoie <code>true</code> s'il écoute, sinon <code>false</code>.</dd>
</dl>

<h2 id="Syntaxe_addListener">Syntaxe addListener</h2>

<h3 id="Paramètres">Paramètres</h3>

<dl>
 <dt><code>callback</code></dt>
 <dd>
 <p>Fonction qui sera appelée lorsque cet événement se produit. La fonction recevra les arguments suivants :</p>

 <dl>
  <dt><code>changeInfo</code></dt>
  <dd><code>object</code>. Un objet qui contient une seule propriété, <code>contextualIdentity</code>, qui est un objet {{WebExtAPIRef("contextualIdentities.ContextualIdentity")}} représentant l'identité qui a été supprimée.</dd>
 </dl>
 </dd>
</dl>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.api.contextualIdentities.onRemoved")}}</p>

<h2 id="Exemples">Exemples</h2>

<pre class="brush: js">function handleRemoved(changeInfo) {
  console.log(`Removed: ${changeInfo.contextualIdentity.name}`);
}

browser.contextualIdentities.onRemoved.addListener(handleRemoved);</pre>

<p>{{WebExtExamples}}</p>

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