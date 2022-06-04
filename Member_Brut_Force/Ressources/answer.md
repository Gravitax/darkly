page : http://localhost:8080/index.php?page=signin

on utilise un dictionnaire de mot de passe trouve sur wikipedia en testant avec des username basique : root, admin

en utilisant le brut force on trouve que le mot de passe est
shadow
l'username est
admin

The flag is : b3a6e43ddf8b4bbb4125e5e7d23040433827759d4de1c04ea63907479a80a6b2


DANGER : 
permettre une escalade de privilege a un utilisateur non root / admin


PROTECTIONS :
Comment se protéger des attaques par force brute
Si vous voulez éviter d'être victime d'une telle attaque, vous pouvez essayer quelques solutions :

Création du mot de passe le plus complexe possible - rien ne garantit que cela vous donnera une sécurité totale, mais cela va aider. Si un mot de passe est trop complexe, les pirates peuvent passer à une cible plus facile. Un mot de passe de 12 à 16 caractères est encore plus sécurisé. Il doit s'agir d'un mélange aléatoire de lettres minuscules, de lettres majuscules, de chiffres et de caractères spéciaux.

Limitation de tentatives de connexion - La solution la plus simple à ce problème consiste à limiter le nombre de tentatives de connexion. Si vous limitez le nombre à 3, vous avez alors trois occasions de saisir le mot de passe correct. Ainsi, si vous vous trompez en vous connectant, vous avez encore deux chances. Après la troisième tentative de connexion, le système verrouille le compte jusqu'à ce qu'il soit vérifié par courriel ou qu'une limite de temps soit atteinte. Cela signifie qu'un pirate informatique n'a que trois chances d'essayer de s'introduire avant que l'alarme ne se déclenche et que le compte ne soit verrouillé.

Activation de la vérification à deux facteurs - Vous pouvez également activer la vérification à deux facteurs. Dans ce cas, les pirates peuvent être en mesure d'utiliser votre force brutale pour obtenir votre mot de passe, mais après l'avoir saisi, ils doivent également entrer un code qui est envoyé à votre téléphone portable ou créé par une application tierce. Pour pirater votre compte, ils devraient voler votre mot de passe ET votre téléphone cellulaire. Certaines applications d’autorisation à deux facteurs courantes sont Google Authenticator, 1Password (sert également de coffre-fort de mot de passe sécurisé), LastPass Authenticator (uniquement pour IOS) et Authy.
