page : http://localhost:8080/?page=e43ad1fdc54babe674da7c7b8f0127bde61de3fbe01def7d00f151c2fcca6d1c
(lien en bas du footer)

si on inspect la page on voit un gros bloc commentaire avec dedans :
"You must cumming from : "https://www.nsa.gov/" to go to the next step"
et
"Let's use this browser : "ft_bornToSec". It will help you a lot."

pour modifier son origine il existe le referer
L'en-tête de requête Referer contient l'adresse de la page web précédente à partir de laquelle un lien a été suivi pour demander la page courante. L'en-tête Referer permet aux serveurs d'identifier la provenance des visiteurs d'une page et cette information peut être utilisée à des fins d'analyse, de journalisation ou pour améliorer la politique de cache par exemple.

pour modifier l'application (le navigateur) que l'on utilise il existe l'User-Agent
The User-Agent request header is a characteristic string that lets servers and network peers identify the application, operating system, vendor, and/or version of the requesting user agent.


we can simulate the reauest with curl :
curl "http://localhost:8080/index.php?page=e43ad1fdc54babe674da7c7b8f0127bde61de3fbe01def7d00f151c2fcca6d1c" -H "User-Agent: ft_bornToSec" -H "Referer: https://www.nsa.gov/" | grep "flag"


DANGER :
permet de changer son origine et donc de ne pas ce faire bloquer par des anti spamm simple
