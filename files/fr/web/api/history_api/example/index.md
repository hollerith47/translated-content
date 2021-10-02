---
title: Exemple de navigation en Ajax
slug: Web/API/History_API/Example
translation_of: Web/API/History_API/Example
original_slug: Web/Guide/DOM/Manipuler_historique_du_navigateur/Example
---
<p>Voici un exemple de site web AJAX composé uniquement de trois pages (<em>page_un.php</em>, <em>page_deux.php</em> et <em>page_trois.php</em>). Pour tester cet exemple, merci de créer les fichiers suivants :</p>

<p><strong>page_un.php</strong>:</p>

<pre class="brush: php">&lt;?php
    $page_title = "Page un";

    $as_json = false;
    if (isset($_GET["view_as"]) &amp;&amp; $_GET["view_as"] == "json") {
        $as_json = true;
        ob_start();
    } else {
?&gt;
&lt;!doctype html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;?php
        include "include/header.php";
        echo "&lt;title&gt;" . $page_title . "&lt;/title&gt;";
?&gt;
&lt;/head&gt;

&lt;body&gt;

&lt;?php include "include/before_content.php"; ?&gt;

&lt;p&gt;This paragraph is shown only when the navigation starts from &lt;strong&gt;first_page.php&lt;/strong&gt;.&lt;/p&gt;

&lt;div id="ajax-content"&gt;
&lt;?php } ?&gt;

    &lt;p&gt;This is the content of &lt;strong&gt;first_page.php&lt;/strong&gt;.&lt;/p&gt;

&lt;?php
    if ($as_json) {
        echo json_encode(array("page" =&gt; $page_title, "content" =&gt; ob_get_clean()));
    } else {
?&gt;
&lt;/div&gt;

&lt;p&gt;This paragraph is shown only when the navigation starts from &lt;strong&gt;first_page.php&lt;/strong&gt;.&lt;/p&gt;

&lt;?php
        include "include/after_content.php";
        echo "&lt;/body&gt;\n&lt;/html&gt;";
    }
?&gt;
</pre>

<p><strong>page_deux.php</strong>:</p>

<pre class="brush: php">&lt;?php
    $page_title = "Page deux";

    $as_json = false;
    if (isset($_GET["view_as"]) &amp;&amp; $_GET["view_as"] == "json") {
        $as_json = true;
        ob_start();
    } else {
?&gt;
&lt;!doctype html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;?php
        include "include/header.php";
        echo "&lt;title&gt;" . $page_title . "&lt;/title&gt;";
?&gt;
&lt;/head&gt;

&lt;body&gt;

&lt;?php include "include/before_content.php"; ?&gt;

&lt;p&gt;This paragraph is shown only when the navigation starts from &lt;strong&gt;second_page.php&lt;/strong&gt;.&lt;/p&gt;

&lt;div id="ajax-content"&gt;
&lt;?php } ?&gt;

    &lt;p&gt;This is the content of &lt;strong&gt;second_page.php&lt;/strong&gt;.&lt;/p&gt;

&lt;?php
    if ($as_json) {
        echo json_encode(array("page" =&gt; $page_title, "content" =&gt; ob_get_clean()));
    } else {
?&gt;
&lt;/div&gt;

&lt;p&gt;This paragraph is shown only when the navigation starts from &lt;strong&gt;second_page.php&lt;/strong&gt;.&lt;/p&gt;

&lt;?php
        include "include/after_content.php";
        echo "&lt;/body&gt;\n&lt;/html&gt;";
    }
?&gt;
</pre>

<p><strong>page_trois.php</strong>:</p>

<pre class="brush: php">&lt;?php
    $page_title = "Page trois";
    $page_content = "&lt;p&gt;Ceci est le contenu de la &lt;strong&gt;page_trois.php&lt;/strong&gt;. Ce contenu est stocké dans une variable PHP.&lt;/p&gt;";

    if (isset($_GET["view_as"]) &amp;&amp; $_GET["view_as"] == "json") {
        echo json_encode(array("page" =&gt; $page_title, "content" =&gt; $page_content));
    } else {
?&gt;
&lt;!doctype html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;?php
        include "include/header.php";
        echo "&lt;title&gt;" . $page_title . "&lt;/title&gt;";
?&gt;
&lt;/head&gt;

&lt;body&gt;

&lt;?php include "include/before_content.php"; ?&gt;

&lt;p&gt;This paragraph is shown only when the navigation starts from &lt;strong&gt;third_page.php&lt;/strong&gt;.&lt;/p&gt;

&lt;div id="ajax-content"&gt;
&lt;?php echo $page_content; ?&gt;
&lt;/div&gt;

&lt;p&gt;This paragraph is shown only when the navigation starts from &lt;strong&gt;third_page.php&lt;/strong&gt;.&lt;/p&gt;

&lt;?php
        include "include/after_content.php";
        echo "&lt;/body&gt;\n&lt;/html&gt;";
    }
?&gt;
</pre>

<p><strong>css/style.css</strong>:</p>

<pre class="brush: css">#ajax-loader {
    position: fixed;
    display: table;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

#ajax-loader &gt; div {
    display: table-cell;
    width: 100%;
    height: 100%;
    vertical-align: middle;
    text-align: center;
    background-color: #000000;
    opacity: 0.65;
}
</pre>
<p><strong>include/after_content.php</strong>:</p>
<pre class="brush: php">&lt;p&gt;Ceci est le pied-de-page. Il est commun à toutes les pages ajax.&lt;/p&gt;
</pre>
<p><strong>include/before_content.php</strong>:</p>
<pre class="brush: php">&lt;p&gt;
[ &lt;a class="ajax-nav" href="page_un.php"&gt;Premier exemple&lt;/a&gt;
| &lt;a class="ajax-nav" href="page_deux.php"&gt;Second exemple&lt;/a&gt;
| &lt;a class="ajax-nav" href="page_trois.php"&gt;Troisième exemple&lt;/a&gt;
| &lt;a class="ajax-nav" href="inexistante.php"&gt;Page inexistante&lt;/a&gt; ]
&lt;/p&gt;

</pre>
<p><strong>include/header.php</strong>:</p>
<pre class="brush: html">&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /&gt;
&lt;script type="text/javascript" src="js/ajax_nav.js"&gt;&lt;/script&gt;
&lt;link rel="stylesheet" href="css/style.css" /&gt;
</pre>
<p><strong>js/ajax_nav.js</strong>:</p>

<pre class="brush: js">"use strict";

var ajaxRequest = new (function () {

    function closeReq () {
        oLoadingBox.parentNode &amp;&amp; document.body.removeChild(oLoadingBox);
        bIsLoading = false;
    }

    function abortReq () {
        if (!bIsLoading) { return; }
        oReq.abort();
        closeReq();
    }

    function ajaxError () {
        alert("Unknown error.");
    }

    function ajaxLoad () {
        var vMsg, nStatus = this.status;
        switch (nStatus) {
            case 200:
                vMsg = JSON.parse(this.responseText);
                document.title = oPageInfo.title = vMsg.page;
                document.getElementById(sTargetId).innerHTML = vMsg.content;
                if (bUpdateURL) {
                    history.pushState(oPageInfo, oPageInfo.title, oPageInfo.url);
                    bUpdateURL = false;
                }
                break;
            default:
                vMsg = nStatus + ": " + (oHTTPStatus[nStatus] || "Unknown");
                switch (Math.floor(nStatus / 100)) {
                    /*
                    case 1:
                        // Informational 1xx
                        console.log("Information code " + vMsg);
                        break;
                    case 2:
                        // Successful 2xx
                        console.log("Successful code " + vMsg);
                        break;
                    case 3:
                        // Redirection 3xx
                        console.log("Redirection code " + vMsg);
                        break;
                    */
                    case 4:
                        /* Client Error 4xx */
                        alert("Client Error #" + vMsg);
                        break;
                    case 5:
                        /* Server Error 5xx */
                        alert("Server Error #" + vMsg);
                        break;
                    default:
                        /* Unknown status */
                        ajaxError();
                }
        }
        closeReq();
    }

    function filterURL (sURL, sViewMode) {
        return sURL.replace(rSearch, "") + ("?" + sURL.replace(rHost, "&amp;").replace(rView, sViewMode ? "&amp;" + sViewKey + "=" + sViewMode : "").slice(1)).replace(rEndQstMark, "");
    }

    function getPage (sPage) {
        if (bIsLoading) { return; }
        oReq = new XMLHttpRequest();
        bIsLoading = true;
        oReq.onload = ajaxLoad;
        oReq.onerror = ajaxError;
        if (sPage) { oPageInfo.url = filterURL(sPage, null); }
        oReq.open("get", filterURL(oPageInfo.url, "json"), true);
        oReq.send();
        oLoadingBox.parentNode || document.body.appendChild(oLoadingBox);
    }

    function requestPage (sURL) {
        if (history.pushState) {
            bUpdateURL = true;
            getPage(sURL);
        } else {
            /* Ajax navigation is not supported */
            location.assign(sURL);
        }
    }

    function processLink () {
        if (this.className === sAjaxClass) {
            requestPage(this.href);
            return false;
        }
        return true;
    }

    function init () {
        oPageInfo.title = document.title;
        for (var oLink, nIdx = 0, nLen = document.links.length; nIdx &lt; nLen; document.links[nIdx++].onclick = processLink);
    }

    const

        /* customizable constants */
        sTargetId = "ajax-content", sViewKey = "view_as", sAjaxClass = "ajax-nav",

        /* not customizable constants */
        rSearch = /\?.*$/, rHost = /^[^\?]*\?*&amp;*/, rView = new RegExp("&amp;" + sViewKey + "\\=[^&amp;]*|&amp;*$", "i"), rEndQstMark = /\?$/,
        oLoadingBox = document.createElement("div"), oCover = document.createElement("div"), oLoadingImg = new Image(),
        oPageInfo = {
            title: null,
            url: location.href
        }, oHTTPStatus = /* http://www.iana.org/assignments/http-status-codes/http-status-codes.xml */ {
            100: "Continue",
            101: "Switching Protocols",
            102: "Processing",
            200: "OK",
            201: "Created",
            202: "Accepted",
            203: "Non-Authoritative Information",
            204: "No Content",
            205: "Reset Content",
            206: "Partial Content",
            207: "Multi-Status",
            208: "Already Reported",
            226: "IM Used",
            300: "Multiple Choices",
            301: "Moved Permanently",
            302: "Found",
            303: "See Other",
            304: "Not Modified",
            305: "Use Proxy",
            306: "Reserved",
            307: "Temporary Redirect",
            308: "Permanent Redirect",
            400: "Bad Request",
            401: "Unauthorized",
            402: "Payment Required",
            403: "Forbidden",
            404: "Not Found",
            405: "Method Not Allowed",
            406: "Not Acceptable",
            407: "Proxy Authentication Required",
            408: "Request Timeout",
            409: "Conflict",
            410: "Gone",
            411: "Length Required",
            412: "Precondition Failed",
            413: "Request Entity Too Large",
            414: "Request-URI Too Long",
            415: "Unsupported Media Type",
            416: "Requested Range Not Satisfiable",
            417: "Expectation Failed",
            422: "Unprocessable Entity",
            423: "Locked",
            424: "Failed Dependency",
            425: "Unassigned",
            426: "Upgrade Required",
            427: "Unassigned",
            428: "Precondition Required",
            429: "Too Many Requests",
            430: "Unassigned",
            431: "Request Header Fields Too Large",
            500: "Internal Server Error",
            501: "Not Implemented",
            502: "Bad Gateway",
            503: "Service Unavailable",
            504: "Gateway Timeout",
            505: "HTTP Version Not Supported",
            506: "Variant Also Negotiates (Experimental)",
            507: "Insufficient Storage",
            508: "Loop Detected",
            509: "Unassigned",
            510: "Not Extended",
            511: "Network Authentication Required"
        };

    var

        oReq, bIsLoading = false, bUpdateURL = false;

    oLoadingBox.id = "ajax-loader";
    oCover.onclick = abortReq;
    oLoadingImg.src = "data:image/gif;base64,R0lGODlhEAAQAPIAAP///wAAAMLCwkJCQgAAAGJiYoKCgpKSkiH/C05FVFNDQVBFMi4wAwEAAAAh/hpDcmVhdGVkIHdpdGggYWpheGxvYWQuaW5mbwAh+QQJCgAAACwAAAAAEAAQAAADMwi63P4wyklrE2MIOggZnAdOmGYJRbExwroUmcG2LmDEwnHQLVsYOd2mBzkYDAdKa+dIAAAh+QQJCgAAACwAAAAAEAAQAAADNAi63P5OjCEgG4QMu7DmikRxQlFUYDEZIGBMRVsaqHwctXXf7WEYB4Ag1xjihkMZsiUkKhIAIfkECQoAAAAsAAAAABAAEAAAAzYIujIjK8pByJDMlFYvBoVjHA70GU7xSUJhmKtwHPAKzLO9HMaoKwJZ7Rf8AYPDDzKpZBqfvwQAIfkECQoAAAAsAAAAABAAEAAAAzMIumIlK8oyhpHsnFZfhYumCYUhDAQxRIdhHBGqRoKw0R8DYlJd8z0fMDgsGo/IpHI5TAAAIfkECQoAAAAsAAAAABAAEAAAAzIIunInK0rnZBTwGPNMgQwmdsNgXGJUlIWEuR5oWUIpz8pAEAMe6TwfwyYsGo/IpFKSAAAh+QQJCgAAACwAAAAAEAAQAAADMwi6IMKQORfjdOe82p4wGccc4CEuQradylesojEMBgsUc2G7sDX3lQGBMLAJibufbSlKAAAh+QQJCgAAACwAAAAAEAAQAAADMgi63P7wCRHZnFVdmgHu2nFwlWCI3WGc3TSWhUFGxTAUkGCbtgENBMJAEJsxgMLWzpEAACH5BAkKAAAALAAAAAAQABAAAAMyCLrc/jDKSatlQtScKdceCAjDII7HcQ4EMTCpyrCuUBjCYRgHVtqlAiB1YhiCnlsRkAAAOwAAAAAAAAAAAA==";
    oCover.appendChild(oLoadingImg);
    oLoadingBox.appendChild(oCover);

    onpopstate = function (oEvent) {
        bUpdateURL = false;
        oPageInfo.title = oEvent.state.title;
        oPageInfo.url = oEvent.state.url;
        getPage();
    };

    window.addEventListener ? addEventListener("load", init, false) : window.attachEvent ? attachEvent("onload", init) : (onload = init);

    // Public methods

    this.open = requestPage;
    this.stop = abortReq;
    this.rebuildLinks = init;

})();
</pre>

<div class="note">
  <p><strong>Note :</strong> <a href="/en/JavaScript/Reference/Statements/const"><code>const</code></a> (instruction de constante) <strong>ne fait pas partie de ECMAScript 5</strong>. Il est supporté dans Firefox et Chrome (V8) et partiellement supporté dans Opera 9+ et Safari. <strong>Il n'est pas supporté dans Internet Explorer 6-9, ou dans la version de prévisualisation de Internet Explorer 10</strong>. <a href="/en/JavaScript/Reference/Statements/const"><code>const</code></a> sera défini par ECMAScript 6, mais avec une sémantique différente. Proches des variables déclarées avec l'instruction <a href="/en/JavaScript/Reference/Statements/let"><code>let</code></a>, les constantes déclarées avec <a href="/en/JavaScript/Reference/Statements/const"><code>const</code></a> seront limitées en portée. <strong>Nous ne l'avons utilisé que pour des raisons pédagogiques, si vous souhaitez une compatibilité maximale de ce code, merci de remplacer les références à </strong><strong><a href="/en/JavaScript/Reference/Statements/const"><code>const</code></a> par des instructions <a href="/en/JavaScript/Reference/Statements/var"><code>var</code></a>.</strong>
  </p>
</div>
<p>Pour plus d'informations, voyez : <a href="/fr/docs/DOM/manipuler_lhistorique_du_navigateur">Manipuler l'historique du navigateur</a>.</p>
<h2 id="Lire_également">Lire également</h2>
<ul>
  <li>{{ domxref("window.history") }}</li>
  <li>{{ domxref("window.onpopstate") }}</li>
</ul>