page : http://localhost:8080/?page=survey

en inspectant on note la presence de fomulaire method post
avec 2 input name : sujet et valeur

curl permet de post des data on utilise donc la commande

curl -d "sujet=10&valeur=10" -X POST "http://localhost:8080/index.php?page=survey" | grep flag

The flag is 03a944b434d5baff05f46c4bede5792551a2595574bcafc9a6e25f67c382ccaa

DANGER :
le probleme ici cest que le formulaire est submit sur un event change de linput
il est donc possible devoyer des donness completement erronees au back (value 50 000 par exemple)
et de creer des comportements indetermines

PROTECTION : 
encore une fois il faut parse les inputs et ne jamais faire confiance a lutilisateur sur les donnees quil va nous envoyer.
