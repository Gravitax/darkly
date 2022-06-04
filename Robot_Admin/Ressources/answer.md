Le protocole d'exclusion des robots souvent nommé robots.txt, est une ressource de format texte qui peut être placée à la racine d'un site web, et qui contient une liste des ressources du site qui ne sont pas censées être indexées par les robots d'indexation des moteurs de recherche. Wikipédia

jai utilise dirb sur mon ordi personnel pour scanner larboressence de ce site

on trouve un robot.txt ainsi quun dossier .hidden et admin

dans robot.txt on trouve un htpasswd qui contient les data 
root:8621ffdbc5698829397d97767ac13db3

on decrypte le pwd et on obitent dragon

sur http://localhost:8080/admin/

root / dragon et
The flag is : d19b4823e0d5600ceed56d5e896ef328d7a2b9e7ac7e80f4fcdb9b10bcb3e7ff


DANGER :
escalade de privileges avec access a des data sensibles


PROTECTION :
htaccess pour empecher laccess a ses dossiers
