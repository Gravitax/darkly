page : http://localhost:8080/index.php?page=feedback

on essais d'injecter du code php, du SQL ou du JS mais rien

on essais de paser un bloc avec un event JS onload dessus
<div onload=alert('test')>script</div>

THE FLAG IS : 0FBB54BBF7D099713CA4BE297E1BC7DA0173D8B3C21C1811B916A3A86652724E


DANGER :
XSS où « Cross-Site Scripting » est l’une des failles les plus répandues dans les sites Web dynamiques. Elle fait partie de la famille des attaques par injection.

une attaque par XSS se produit lorsqu’un utilisateur mal intentionné envoie un code nuisible qui sera exécuté par le navigateur ou l’interpréteur de la victime (HTML, XML, Flash, JavaScript, CSS, JSON, etc.) en utilisant des formulaires ou directement l’URL. L’exploitation de cette faille permettrait notamment d’exécuter des scripts douteux (dans le cas d’une injection JavaScript), de récupérer les informations récoltées sur un serveur distant (cookies, contenu de la page, etc.), de rediriger la victime, de défigurer la structure de la page, etc.

PROTECTON :
ne jamais trust les donnees recues d'un utilisateur. parse les URLs si on doit les utiliser (regex, escapeString etc)
