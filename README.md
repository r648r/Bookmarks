# Bookmarks
Some dope content


## À propos de l'API CDX de Wayback Machine

L'API CDX (Capture inDeX) permet d'accéder aux métadonnées des captures de la Wayback Machine. Les paramètres utilisés sont :
- `url=*.domaine` : recherche toutes les URL du domaine
- `fl=original` : affiche uniquement les URL originales
- `collapse=urlkey` : évite les doublons
- `output=text` : format de sortie texte (utilisé dans plusieurs bookmarklets)
- `filter=original:.*pattern` : filtre les résultats selon des patterns spécifiques### Bookmarklet - Extracteur de Scripts Inline## Catégorie 2 : Gestion des Hostnames## Catégorie 4 : Outils de Vérification DNS et Sécurité

### Bookmarklet - Vérification DNS ViewDNS.info

#### Code

	javascript:(function(){
		"use strict";
		window.open('https://viewdns.info/iphistory/?domain='+encodeURIComponent(location.hostname));
		window.open('https://viewdns.info/dnsreport/?domain='+encodeURIComponent(location.hostname))
	})()
[DNS ViewDNS.info](javascript%3A%28function%28%29%7B%22use%20strict%22%3Bwindow.open%28%27https%3A%2F%2Fviewdns.info%2Fiphistory%2F%3Fdomain%3D%27%2BencodeURIComponent%28location.hostname%29%29%3Bwindow.open%28%27https%3A%2F%2Fviewdns.info%2Fdnsreport%2F%3Fdomain%3D%27%2BencodeURIComponent%28location.hostname%29%29%7D%29%28%29)
#### Explication rapide

Ouvre deux onglets avec ViewDNS.info pour vérifier l'historique IP et le rapport DNS complet du domaine actuel.

### Bookmarklet - Analyse SSL Labs

#### Code

	javascript:(function(){
		"use strict"; 
		location.href = 'https://www.ssllabs.com/ssltest/analyze.html?d=' + encodeURIComponent(location.hostname); 
	})()

#### Explication rapide

Redirige vers l'outil d'analyse SSL de Qualys SSL Labs pour vérifier la configuration SSL/TLS du site actuel.### Bookmarklet - Recherche de fichiers de sauvegarde

#### Code

	javascript:(function() {
		var currentURL = encodeURIComponent(window.location.hostname.replace(/^www\./, ''));
		var newURL = 'https://web.archive.org/cdx/search/cdx?url=*.' + currentURL +
				   '&fl=original&collapse=urlkey&output=text&filter=original:.*[.](bak|old|tmp|save)';
		window.open(newURL, '_blank');
	})();

#### Explication rapide

Recherche dans Wayback Machine les fichiers de sauvegarde potentiellement exposés (BAK, OLD, TMP, SAVE).

### Bookmarklet - Recherche d'archives compressées

#### Code

	javascript:(function() {
		var currentURL = encodeURIComponent(window.location.hostname.replace(/^www\./, ''));
		var newURL = 'https://web.archive.org/cdx/search/cdx?url=*.' + currentURL +
				   '&fl=original&collapse=urlkey&output=text&filter=original:.*[.](zip|rar|7z|gz)';
		window.open(newURL, '_blank');
	})();

#### Explication rapide

Recherche dans Wayback Machine les fichiers d'archives compressées (ZIP, RAR, 7Z, GZ).# Documentation des Bookmarklets

## Catégorie 1 : Recherche dans Wayback Machine

Ces bookmarklets permettent de rechercher rapidement dans les archives de la Wayback Machine toutes les URL associées au domaine que vous visitez actuellement.

### Bookmarklet - Recherche sans fichiers HTML/HTM

### Code

	javascript:(function() { 
		var currentURL = encodeURIComponent(window.location.hostname.replace(/^www\./, '')); 
		var newURL = 'https://web.archive.org/cdx/search/cdx?url=*.' + currentURL + '&fl=original&collapse=urlkey&output=text&filter=!original:.*[.](html|htm)$'; 
		window.open(newURL, '_blank'); 
	})();

### Explication rapide

1. Récupère le nom de domaine actuel et supprime le préfixe "www." s'il existe
2. Encode l'URL pour une utilisation sécurisée dans une requête
3. Construit une URL pour l'API CDX de Wayback Machine avec exclusion des fichiers HTML/HTM
4. Ouvre cette URL dans un nouvel onglet

### Utilisation

Ajoutez ce code comme favori dans votre navigateur en créant un nouveau marque-page et en collant le code dans le champ URL. Cliquez sur ce favori lorsque vous êtes sur un site web pour voir toutes les archives non-HTML de ce domaine.

### Bookmarklet - Recherche complète

### Code

	javascript:(function() { 
		var currentURL = encodeURIComponent(window.location.hostname.replace(/^www\./, '')); 
		var newURL = 'https://web.archive.org/cdx/search/cdx?url=*.' + currentURL + '&fl=original&collapse=urlkey'; 
		window.open(newURL, '_blank'); 
	})();

### Explication rapide

1. Récupère le nom de domaine actuel et supprime le préfixe "www." s'il existe
2. Encode l'URL pour une utilisation sécurisée dans une requête
3. Construit une URL pour l'API CDX de Wayback Machine sans filtre d'exclusion
4. Ouvre cette URL dans un nouvel onglet



### Bookmarklet - Recherche des URLs avec paramètres

#### Code

	javascript:(function() {
		var currentURL = encodeURIComponent(window.location.hostname.replace(/^www\./, ''));
		var newURL = 'https://web.archive.org/cdx/search/cdx?url=*.' + currentURL +
				   '&fl=original&collapse=urlkey&output=text&filter=original:.*\\?.*=.*';
		window.open(newURL, '_blank');
	})();

#### Explication rapide

Recherche dans Wayback Machine uniquement les URLs contenant des paramètres de requête (URLs avec "?").

### Bookmarklet - Recherche de scripts côté serveur

#### Code

	javascript:(function() {
		var currentURL = encodeURIComponent(window.location.hostname.replace(/^www\./, ''));
		var newURL = 'https://web.archive.org/cdx/search/cdx?url=*.' + currentURL +
				   '&fl=original&collapse=urlkey&output=text&filter=original:.*[.](php|aspx|asp|jsp|cgi|ashx)';
		window.open(newURL, '_blank');
	})();

#### Explication rapide

Recherche dans Wayback Machine les fichiers de scripts côté serveur (PHP, ASPX, ASP, JSP, CGI, ASHX).

### Bookmarklet - Recherche de scripts côté client

#### Code

	javascript:(function() {
		var currentURL = encodeURIComponent(window.location.hostname.replace(/^www\./, ''));
		var newURL = 'https://web.archive.org/cdx/search/cdx?url=*.' + currentURL +
				   '&fl=original&collapse=urlkey&output=text&filter=original:.*[.](js|jsonp|jsx|ts|tsx)';
		window.open(newURL, '_blank');
	})();

#### Explication rapide

Recherche dans Wayback Machine les fichiers de scripts JavaScript et TypeScript (JS, JSONP, JSX, TS, TSX).

### Bookmarklet - Collecteur de Hostnames

#### Code

	javascript:(function(){
		const e=document.querySelectorAll("li.hostnames.text-secondary");
		if(0===e.length)return void alert("Aucun %C3%A9l%C3%A9ment trouv%C3%A9 avec le s%C3%A9lecteur sur cette page");
		const t=Array.from(e).map(e=>e.textContent.trim()).filter(e=>e.length>0);
		let n=[];
		try{
			const e=localStorage.getItem("raphdan_hostnames");
			e&&(n=JSON.parse(e))
		}catch(e){
			console.error("Erreur:",e)
		}
		const a=Array.from(new Set([...n,...t])).sort((e,t)=>e.localeCompare(t,"fr",{sensitivity:"base"}));
		localStorage.setItem("raphdan_hostnames",JSON.stringify(a));
		const o=window.open("","_blank");
		o.document.write(`<html><head><title>raphdan - Hostnames (${a.length})</title><style>body{font-family:monospace;background:#f0f0f0}pre{background:white;padding:10px;border:1px%20solid%20#ccc}.info{color:#800020;margin-bottom:10px}</style></head><body><div%20class="info"><b>${t.length}</b>%20hostnames%20trouv%C3%A9s%20sur%20cette%20page,%20<b>${a.length}</b>%20hostnames%20au%20total%20stock%C3%A9s.</div><pre>${a.join("\n")}</pre></body></html>`),
		o.document.close()
	})();

#### Explication rapide

Collecte les hostnames depuis les éléments "li.hostnames.text-secondary", les sauvegarde dans localStorage et affiche un rapport détaillé.

### Bookmarklet - Suppression des Hostnames

#### Code

	javascript:(function(){
		const e=JSON.parse(localStorage.getItem("raphdan_hostnames")||"[]").length;
		confirm(`Voulez-vous vraiment supprimer les ${e} hostnames sauvegard%C3%A9s ?`)&&(localStorage.removeItem("raphdan_hostnames"),alert("Liste de hostnames supprim%C3%A9e avec succ%C3%A8s!"))
	})();

#### Explication rapide

Supprime tous les hostnames sauvegardés après confirmation de l'utilisateur.

## Catégorie 3 : Analyse de Framework

### Bookmarklet - Analyseur Next.js

#### Code

	javascript:(function(){
		try{
			var s=document.querySelectorAll('script:not([src])'),c=[],i,t=0;
			for(i=0;i<s.length;i++)c.push(s[i].innerHTML);
			if(c.length===0){alert("No inline scripts found on this page.");return}
			for(i=0;i<c.length;i++)t+=c[i].length;
			var w=window.open('about:blank','_blank');
			var h='<!DOCTYPE html><html><head><style>body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen-Sans,Ubuntu,Cantarell,"Helvetica Neue",sans-serif;background:#f5f5f5;color:#333;line-height:1.5;margin:0;padding:20px}h2{color:#2c3e50;border-bottom:2px solid #3498db;padding-bottom:8px;margin-top:25px}h3{color:#34495e;margin:15px 0 8px}textarea{background:#fff;border:1px solid #ddd;border-radius:4px;padding:8px;font-family:Consolas,Monaco,"Andale Mono",monospace;box-shadow:inset 0 1px 2px rgba(0,0,0,.1);transition:border .3s ease,box-shadow .3s ease;resize:vertical}textarea:focus{outline:none;border-color:#3498db;box-shadow:inset 0 1px 2px rgba(0,0,0,.1),0 0 6px rgba(52,152,219,.3)}hr{border:0;height:1px;background:#ddd;margin:20px 0}.container{max-width:900px;margin:0 auto;background:#fff;padding:25px;border-radius:5px;box-shadow:0 2px 10px rgba(0,0,0,.1)}.header{text-align:center;margin-bottom:25px}.script-box{background:#f9f9f9;border-radius:4px;padding:15px;margin-bottom:20px;border-left:4px solid #3498db}.copy-hint{color:#888;font-size:12px;margin-top:5px;font-style:italic}.all-scripts{background:#2c3e50;color:#ecf0f1;padding:15px;border-radius:5px;margin-bottom:30px}.all-scripts h2{color:#ecf0f1;border-bottom-color:#3498db}.all-scripts textarea{background:#34495e;color:#ecf0f1;border-color:#2c3e50}</style></head><body><div class="container"><div class="header"><h2>🔍 '+c.length+' inline scripts found</h2></div>';
			h+='<div class="all-scripts"><h2>Inline Js - ALL ('+t+' characters)</h2><textarea readonly rows="10" style="width:100%;">'+c.join('\n\n---\n\n')+'</textarea><div class="copy-hint" style="color:#bbb;">Click in textarea and press Ctrl+A then Ctrl+C to copy</div></div>';
			for(i=0;i<c.length;i++){
				var n=c[i].length;
				h+='<div class="script-box"><h3>Inline Js #'+(i+1)+' ('+n+' characters)</h3><textarea readonly rows="6" style="width:100%;">'+c[i]+'</textarea><div class="copy-hint">Click in textarea and press Ctrl+A then Ctrl+C to copy</div></div>'
			}
			h+='</div></body></html>';
			w.document.write(h);
			w.document.close()
		}catch(e){
			alert("Error: "+e.message)
		}
	})();

#### Explication rapide

Extrait tous les scripts JavaScript inline (sans attribut src) de la page courante et les affiche dans une interface formatée pour faciliter l'analyse.

#### Code

	javascript:(function(){
		var a=window.location.hostname;
		var b=window.location.origin;
		var c=Array.from(document.querySelectorAll("script[src]")).map(function(a){return a.getAttribute("src")});
		var d=c.filter(function(a){return a.includes("_next/static/")||a.includes("next/static/")||a.includes("chunks/")});
		var e=null;
		for(var f=0;f<d.length;f++){
			var g=d[f].match(/_next\/static\/([^/?]+)\//);
			if(g&&g[1]&&g[1]!=="chunks"){e=g[1];break}
		}
		var h=[];
		var i=d.some(function(a){return a.includes("%5B...")||a.includes("[...")});
		if(i){h.push("[...slug] (route attrape-tout)")}
		for(var j=0;j<d.length;j++){
			if(d[j].includes("pages/")){
				var k=d[j].match(/pages\/([^.]+)\.(js|ts)/);
				if(k){h.push("/"+k[1].replace(/\[(.+?)\]/g,":$1"))}
			}
			var l=d[j].match(/pages[-_]([a-z0-9-_]+)/i);
			if(l){h.push("/"+l[1].replace(/-/g,"/"))}
		}
		var m=window.open("","_blank");
		m.document.write("<html><head><title>Next.js Analyse - "+a+"</title><style>body{font-family:monospace;margin:20px}h1,h2{margin-bottom:15px}.box{padding:15px;background:#f5f5f5;border-radius:5px;margin-bottom:20px}.note{background:#fffde7;padding:10px;border-left:4px%20solid%20#ffeb3b;margin:10px%200}pre{background:#f9f9f9;padding:10px;overflow-x:auto}</style></head><body><h1>Analyse%20Next.js%20pour%20"+a+"</h1><div%20class=\"box\"><h2>Informations%20de%20base</h2><p>Site:%20"+b+"</p><p>Build%20ID:%20"+(e||"Non%20d%C3%A9tect%C3%A9")+"</p></div><div%20class=\"box\"><h2>Scripts%20Next.js%20d%C3%A9tect%C3%A9s%20("+d.length+")</h2><pre>"+d.map(function(a){return%20a.startsWith("/")?b+a:a}).join("\n")+"</pre></div><div%20class=\"box\"><h2>Routes%20potentielles%20("+h.length+")</h2>"+(i?"<div%20class=\"note\"><strong>Note:</strong>%20Une%20route%20dynamique%20[...slug]%20a%20%C3%A9t%C3%A9%20d%C3%A9tect%C3%A9e.%20Cette%20route%20sp%C3%A9ciale%20peut%20g%C3%A9rer%20pratiquement%20tous%20les%20chemins%20sur%20le%20site.%20C'est%20pourquoi%20peu%20de%20routes%20sp%C3%A9cifiques%20sont%20identifiables.</div>":"")+"<ul>"+h.map(function(a){return"<li>"+a+"</li>"}).join("")+"</ul></div><div%20class=\"box\"><h2>Comment%20explorer%20davantage</h2><p>URLs%20%C3%A0%20essayer%20manuellement:</p><ul>"+(e?"<li><a%20href=\""+b+"/_next/static/"+e+"/_buildManifest.js\"%20target=\"_blank\">BuildManifest</a></li>":"")+"<li><a%20href=\""+b+"/_next/static/routes-manifest.json\"%20target=\"_blank\">Routes%20Manifest</a></li>"+(i?"<li>Essayez%20diff%C3%A9rents%20chemins%20sur%20le%20site,%20car%20la%20route%20[...slug]%20peut%20g%C3%A9rer%20de%20nombreuses%20URLs</li>":"")+"</ul></div></body></html>");
		m.document.close()
	})();

#### Explication rapide

Analyse le site web actuel pour détecter s'il utilise Next.js, affiche les routes, le build ID et propose des liens pour explorer davantage.
