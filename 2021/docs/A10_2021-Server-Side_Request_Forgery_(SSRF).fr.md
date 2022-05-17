# A10:2021 – A10 Falsification de requête côté serveur (SSRF)    ![icon](assets/TOP_10_Icons_Final_SSRF.png){: style="height:80px;width:80px" align="right"}

## Facteurs

| CWEs associées | Taux d'incidence max | Taux d'incidence moyen | Exploitation pondérée moyenne | Impact pondéré moyen | Couverture max | Couverture moyenne | Nombre total d'occurrences | Nombre total de CVEs |
|:--------------:|:--------------------:|:----------------------:|:-----------------------------:|:--------------------:|:--------------:|:------------------:|:--------------------------:|:--------------------:|
|       1        |        2,72 %        |         2,72 %         |             8,28              |         6,72         |    67,72 %     |      67,72 %       |           9 503            |         385          |

## Aperçu

Cette catégorie est ajoutée à partir de l'enquête communautaire Top 10 (n°1). Les données montrent un taux d'incidence relativement faible avec une couverture de test supérieure à la moyenne et des évaluations du potentiel d'exploitation et d'impact supérieures à la moyenne. Comme les nouvelles entrées sont susceptibles d'être une seule ou un petit groupe de *Common Weakness Enumerations* (CWE) pour l'attention et la sensibilisation, l'espoir est qu'elles fassent l'objet d'une attention particulière et qu'elles puissent être intégrées dans une catégorie plus importante dans une prochaine édition.

## Description 

Une faille SSRF se produit lorsqu'une application web récupère une ressource distante sans valider l'URL fournie par l'utilisateur. Elle permet à un attaquant de contraindre l'application à envoyer une requête élaborée à une destination inattendue, même si elle est protégée par un pare-feu, un VPN ou un autre type de liste de contrôle d'accès au réseau (ACL).

Comme les applications Web modernes offrent aux utilisateurs finaux des fonctions pratiques, la récupération d'une URL devient un scénario courant. Par conséquent, l'incidence d'une SSRF augmente. De même, la gravité de ce phénomène augmente en raison des services en nuage et de la complexité des architectures.

## Comment s'en prémunir

Les développeurs peuvent prévenir ce type de vulnérabilité en mettant en œuvre tout ou partie des contrôles de défense en profondeur suivants :

### **Couche réseau :**

- segmenter la fonctionnalité d'accès aux ressources à distance dans des réseaux distincts pour réduire l'impact d'une SSRF ;
- appliquer des politiques de pare-feu ou des règles de contrôle d'accès au réseau "refusant par défaut" afin de bloquer tout le trafic intranet sauf celui qui est essentiel.<br/> 
    *Conseils:*<br> 
    - Établir une propriété et un cycle de vie pour les règles du pare-feu en fonction des applications.<br/>
    - Consigner tous les flux réseau acceptés *et* bloqués sur les pare-feu (voir [A09:2021-Carence des systèmes de contrôle et de journalisation](A09_2021-Security_Logging_and_Monitoring_Failures.md)).

### **Couche applicative :**

- assainir et valider toutes les données d'entrée fournies par le client ;
- imposer le schéma d'URL, le port et la destination avec une liste positive d'autorisation ;
- ne pas envoyer de réponses brutes aux clients ;
- désactiver les redirections HTTP ;
- veiller à la cohérence des URL pour éviter les attaques telles que le rebinding DNS et les situations de concurrence de type "time of check, time of use" (TOCTOU).

N'atténuez pas les SSRF par l'utilisation d'une liste de refus ou d'une expression régulière. Les attaquants disposent de dictionnaires, d'outils et de compétences pour contourner les listes de refus.

### **Mesures complémentaires :**

- ne pas déployer d'autres services liés à la sécurité sur les systèmes frontaux (par exemple, OpenID). Contrôlez le trafic local sur ces systèmes (par exemple, localhost) ;
- pour les frontaux avec des groupes d'utilisateurs dédiés et gérables, utilisez le chiffrement du réseau (par exemple, les VPN) sur des systèmes indépendants pour prendre en compte les besoins de protection très élevés.

## Exemple de scénarios d'attaque

Les attaquants peuvent utiliser SSRF pour attaquer des systèmes protégés derrière des pare-feu d'applications web, des pare-feu ou des ACL de réseau, en utilisant des scénarios tels que :

**Scénario n°1 :** Analyse des ports des serveurs internes - Si l'architecture du réseau n'est pas segmentée, les attaquants peuvent cartographier les réseaux internes et déterminer si les ports sont ouverts ou fermés sur les serveurs internes à partir des résultats de connexion ou du temps écoulé pour connecter ou les connexions rejetées avec une charge utile de type SSRF.

**Scénario n°2 :** Exposition de données sensibles - Les attaquants peuvent accéder aux fichiers locaux ou aux services internes pour obtenir des informations sensibles telles que `file:///etc/passwd` et `http://localhost:28017/`.

**Scénario n°3 :** Accéder au stockage des métadonnées des services en nuage - La plupart des fournisseurs d'informatique en nuage ont un stockage de métadonnées tel que `http://169.254.169.254/`. Un attaquant peut lire les métadonnées pour obtenir des informations sensibles.

**Scénario n°4 :** Compromettre les services internes - L'attaquant peut abuser des services internes pour mener d'autres attaques telles que l'exécution de code à distance (RCE) ou le déni de service (DoS).

## Références

-   [OWASP - Server-Side Request Forgery Prevention Cheat
    Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html)

-   [PortSwigger - Server-side request forgery
    (SSRF)](https://portswigger.net/web-security/ssrf)

-   [Acunetix - What is Server-Side Request Forgery
    (SSRF)?](https://www.acunetix.com/blog/articles/server-side-request-forgery-vulnerability/)

-   [SSRF
    bible](https://cheatsheetseries.owasp.org/assets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet_SSRF_Bible.pdf)

-   [A New Era of SSRF - Exploiting URL Parser in Trending Programming
    Languages!](https://www.blackhat.com/docs/us-17/thursday/us-17-Tsai-A-New-Era-Of-SSRF-Exploiting-URL-Parser-In-Trending-Programming-Languages.pdf)

## Liste des CWEs associées

[CWE-918 Server-Side Request Forgery (SSRF)](https://cwe.mitre.org/data/definitions/918.html)
