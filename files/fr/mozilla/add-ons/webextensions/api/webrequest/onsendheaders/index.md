---
title: webRequest.onSendHeaders
slug: Mozilla/Add-ons/WebExtensions/API/webRequest/onSendHeaders
tags:
  - API
  - Add-ons
  - Event
  - Extensions
  - Non-standard
  - Reference
  - WebExtensions
  - onSendHeaders
  - webRequest
translation_of: Mozilla/Add-ons/WebExtensions/API/webRequest/onSendHeaders
---
<div>{{AddonSidebar()}}</div>

<p>Cet événement est déclenché juste avant l'envoi des en-têtes. Si votre extension ou une autre extension a modifié les en-têtes dans  <code>{{WebExtAPIRef("webRequest.onBeforeSendHeaders", "onBeforeSendHeaders")}}</code>, vous verrez la version modifiée ici.</p>

<p>Cet événement est à titre d'information seulement.</p>

<h2 id="Syntaxe">Syntaxe</h2>

<pre class="brush: js">browser.webRequest.onSendHeaders.addListener(
  listener,             // function
  filter,               //  object
  extraInfoSpec         //  optional array of strings
)
browser.webRequest.onSendHeaders.removeListener(listener)
browser.webRequest.onSendHeaders.hasListener(listener)
</pre>

<p>Les événements ont trois fonctions :</p>

<dl>
 <dt><code>addListener(callback, filter, extraInfoSpec)</code></dt>
 <dd>Ajouter un auditeur à cet événement.</dd>
 <dt><code>removeListener(listener)</code></dt>
 <dd>Arrêtez d'écouter cet événement. L'argument <code>listener</code> est l'auditeur à supprimer.</dd>
 <dt><code>hasListener(listener)</code></dt>
 <dd>Vérifiez si <code>listener</code> est enregistré à cet événement. Retourne <code>true</code> s'il est écouté, sinon <code>false</code>.</dd>
</dl>

<h2 id="Syntaxe_addListener">Syntaxe addListener</h2>

<h3 id="Paramètres">Paramètres</h3>

<dl>
 <dt><code>callback</code></dt>
 <dd>
 <p>Fonction qui sera appelée lorsque cet événement se produira. La fonction sera passée les arguments suivants :</p>

 <dl>
  <dt><code>details</code></dt>
  <dd><a href="#details"><code>object</code></a>. Détails sur la demande. Voir les <code><a href="#details">details</a></code> ci-dessous.</dd>
 </dl>
 </dd>
 <dt><code>filter</code></dt>
 <dd>{{WebExtAPIRef('webRequest.RequestFilter')}}. Un filtre qui restreint les événements qui seront envoyés à cet auditeur.</dd>
 <dt><code>extraInfoSpec</code>{{optional_inline}}</dt>
 <dd><p><code>array</code> de <code>string</code>. Options supplémentaires pour l'événement. Vous ne pouvez passer qu'une seule valeur ici :</p>
 <ul>
  <li><code>"requestHeaders"</code>: inclure les en-têtes de requête dans l'objet détails transmis à l'auditeur</li>
 </ul>
 </dd>
</dl>

<h2 id="Objets_supplémentaires">Objets supplémentaires</h2>

<h3 id="détails">détails</h3>

<dl>
 <dt><code>documentUrl</code></dt>
 <dd><code>string</code>. URL du document dans lequel la ressource sera chargée. Par exemple, si la page web "https://example.com" contient une image ou un iframe, alors le <code>documentUrl</code> pour l'image ou l'iframe sera "https://example.com". Pour un document de niveau supérieur, <code>documentUrl</code> n'est pas défini.</dd>
 <dt><code>frameId</code></dt>
 <dd><code>integer</code>. Zéro si la requête se produit dans le cadre principal ; une valeur positive est l'ID d'une sous-trame dans laquelle la requête se produit. Si le document d'un (sous-)cadre est chargé (<code>type</code> is <code>main_frame</code> or <code>sub_frame</code>), <code>frameId</code> indique l'ID de ce cadre et non l'ID du cadre extérieur. Les ID de trame sont uniques dans un onglet.</dd>
 <dt><code>method</code></dt>
 <dd><code>string</code>. Méthode HTTP standard : par exemple, "GET" ou "POST".</dd>
 <dt><code>originUrl</code></dt>
 <dd>
 <p><code>string</code>. URL de la ressource qui a déclenché la requête. Par exemple, si "https://example.com" contient un lien, et que l'utilisateur clique sur le lien, alors <code>originUrl</code> de la requête résultante est "https://example.com".</p>

 <p>L'<code>originUrl</code> est souvent mais pas toujours la même chose que <code>documentUrl</code>.Par exemple, si une page contient une iframe, et que l'iframe contient un lien qui charge un nouveau document dans l'iframe, alors le <code>documentUrl</code> pour la requête résultante sera le document parent de l'iframe, mais l'<code>originUrl</code> sera l'URL du document dans l'iframe qui contenait le lien.</p>
 </dd>
 <dt><code>parentFrameId</code></dt>
 <dd><code>integer</code>. de la trame qui contient la trame qui a envoyé la requête. Réglé à -1 s'il n'existe pas de l'iframe parent.</dd>
 <dt><code>proxyInfo</code></dt>
 <dd>
 <p><code>object</code>. Cette propriété n'est présente que si la demande est proxied. Il contient les propriétés suivantes :</p>

 <dl>
  <dt><code>host</code></dt>
  <dd><code>string</code>. Le nom d'hôte du serveur proxy.</dd>
  <dt><code>port</code></dt>
  <dd><code>integer</code>. Le numéro de port du serveur proxy.</dd>
  <dt><code>type</code></dt>
  <dd>
  <p><code>string</code>. Le type de serveur proxy. L'un des :</p>

  <ul>
   <li>"http": proxy HTTP (ou SSL CONNECT pour HTTPS)</li>
   <li>"https": proxy HTTP sur connexion TLS vers proxy</li>
   <li>"socks": SOCKS v5 proxy</li>
   <li>"socks4": SOCKS v4 proxy</li>
   <li>"direct": pas de proxy</li>
   <li>"unknown": proxy inconnu</li>
  </ul>
  </dd>
  <dt><code>username</code></dt>
  <dd><code>string</code>. Nom d'utilisateur pour le service proxy.</dd>
  <dt><code>proxyDNS</code></dt>
  <dd><code>boolean</code>. Vrai si le proxy exécutera une résolution de nom de domaine basée sur le nom d'hôte fourni, ce qui signifie que le client ne doit pas faire sa propre recherche DNS.</dd>
  <dt><code>failoverTimeout</code></dt>
  <dd><code>integer</code>. Délai d'attente de basculement en secondes. Si la connexion par proxy échoue, le proxy ne sera pas utilisé à nouveau pendant cette période.</dd>
 </dl>
 </dd>
 <dt><code>requestId</code></dt>
 <dd><code>string</code>. L'ID de la demande. Les ID de requête sont uniques au sein d'une session de navigateur, de sorte que vous pouvez les utiliser pour relier différents événements associés à la même requête.</dd>
 <dt><code>requestHeaders</code>{{optional_inline}}</dt>
 <dd>{{WebExtAPIRef('webRequest.HttpHeaders')}}. Les en-têtes de réponse HTTP qui ont été reçus avec cette réponse.</dd>
 <dt><code>tabId</code></dt>
 <dd><code>integer</code>. ID de l'onglet dans lequel la demande a lieu. Définir à -1 si la requête n'est pas liée à un onglet.</dd>
 <dt><code>timeStamp</code></dt>
 <dd><code>number</code>. L'heure à laquelle cet événement s'est déclenché, en <a href="https://en.wikipedia.org/wiki/Unix_time">millisecondes depuis l'époque</a>.</dd>
 <dt><code>type</code></dt>
 <dd>{{WebExtAPIRef('webRequest.ResourceType')}}. Le type de ressource demandée : par exemple, "image", "script", "stylesheet".</dd>
 <dt><code>url</code></dt>
 <dd><code>string</code>. Cible de la demande.</dd>
</dl>

<h2 id="Compatibilité_du_navigateur">Compatibilité du navigateur</h2>

<p>{{Compat("webextensions.api.webRequest.onSendHeaders", 10)}}</p>

<h2 id="Exemples">Exemples</h2>

<p>Ce code enregistre tous les cookies qui seront envoyés en faisant des demandes au <a href="/fr/docs/Mozilla/Add-ons/WebExtensions/Match_patterns">modèle de match</a> cible :</p>

<pre class="brush: js">// The target match pattern
var targetPage = "*://*.google.ca/*";

// Log cookies sent with this request
function logCookies(e) {
  for (var header of e.requestHeaders) {
    if (header.name == "Cookie") {
      console.log(header.value);
    }
  }
}

// Listen for onSendHeaders, and pass
// "requestHeaders" so we get the headers
browser.webRequest.onSendHeaders.addListener(
  logCookies,
  {urls: [targetPage]},
  ["requestHeaders"]
);</pre>

<p>{{WebExtExamples}}</p>

<div class="note"><p><strong>Note :</strong></p>

<p>Cette API est basée sur l'API Chromium <a href="https://developer.chrome.com/extensions/webRequest"><code>chrome.webRequest</code></a>. Cette documentation est dérivée de <a href="https://chromium.googlesource.com/chromium/src/+/master/extensions/common/api/web_request.json"><code>web_request.json</code></a> dans le code Chromium.</p>

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