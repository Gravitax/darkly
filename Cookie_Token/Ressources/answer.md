en faisant inspecter : application : Cookies
on trouve un token I_am_admin

on decrypte le token
68934a3e9455fa72420237eb05902327 : false

on le modifie
Md5(true) = b326b5062b2f0e69046810717534cb09

on essais dacceder a la page membre et une alert apparait

Good job! Flag : df2eb4ba34ed059a1e3e89ff4dfc13445f104a1a52295214def1c4fb1693a5c3


DANGER :
escalade de privileges


PROTECTION :
complexifier les mots de passe
utiliser JWT
JSON Web Token
JSON Web Token est un standard ouvert défini dans la RFC 7519. Il permet l'échange sécurisé de jetons entre plusieurs parties. Cette sécurité de l’échange se traduit par la vérification de l'intégrité et de l'authenticité des données. Elle s’effectue par l'algorithme HMAC ou RSA.
