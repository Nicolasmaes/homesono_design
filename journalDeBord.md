# Journal de bord

## Mise à jour le 14/04/22

Cette semaine voici où en est le projet : 

-  ### API
    - L'écriture de l'API est très avancée
    - Toutes les entités sont écrites
    - Le controller principal est écrit (CRUD sur les tables principales)
    - Je dois encore séparer le controller en plusieurs petits controller selon chaque entités.
    - JWT : définir le token avec une durée assez courte, car une fois qu’on a distribué un token on ne peut pas le révoquer, donc l’utilisateur restera connecté, on ne peut pas le déconnecter nous-mêmes.
- ### Front-end
    - Les bases sont posées en React.
    - Après avoir essayé Vite (avec React), je suis revenu sur mes pas car impossible de travailler avec du CSS comme je le veux.
    - Au 14/04, je dois encore établir une bonne connexion entre le front et Redux. 
- ### Conception
    - Pas encore de maquette
    - J'ai pas encore réfléchi aux visuels précis, mais l'app ressemblera à un site e-commerce classique.

    
## Mise à jour le 23/08/22

Cette semaine voici où en est le projet : 

-  ### API
    - La sécurité avec JWT est en place, je dois encore faire en sorte qu'on puisse se connecter avec un user présent en base
    - Je dois désormais mettre en place les annotations @RolesAllowed pour sécuriser les routes.

- ### Front-end
    - Le projet est prêt pour implémenter les vues.
    - J'utilise React avec Ionic
    - Redux est en place, et je travaille déjà avec.
    - La connexion fonctionne presque parfaitement (inscription, déconnexion)
    - Le menu est personnalisé selon que l'on soit connecté ou non à l'appli, je dois encore le personnaliser selon l'utilsateur admin ou un user classique.
    
- ### Conception
    - Pas encore de maquette
    - J'ai regardé les apps des grands commerçants (Amazon, Fnac, McDonald's, Decathlon, Sushi Shop, Burger King...)
    - Presque toutes ont en commun un navigation avec des onglets en bas de page, dans laquelle on retrouve la page d'accueil, le compte du client, le panier, les favoris, la zone de recherche, la liste des points de vente, les actualités...
    #### Donc ça me semble être un bon début d'afficher dans HomeSono ces 4 onglets en bas : 
        - Accueil 
        - Recherche
        - Compte
        - Panier

        faire marcher @RolesAllowed
        envoyer le role back dans le token (admin ou user) pour bien custom le front
        
        Ajouter des captures d'écrans du code d'APRR et des apps APRR sur lesquelles j'ai travaillé
Jenkins etc...

avoir des notes de powerpoint pendant la diffusion
        puis-je utiliser notion pour presenter des trucs ?
        ou doit-on rester dans la trame de notre rapport et le suivre ? OUI

        Parler de react qui s'occupe d'empecher les injections de code dans les input faille XSS

        Spring security
        Restreindre des accès dans le front (affichage et acces), et dans le back (au niveau des routes)

        https://www.baeldung.com/role-and-privilege-for-spring-security-registration

        https://www.baeldung.com/spring-security-method-security

        @QueryParam is a JAX-RS framework annotation and @RequestParam is from Spring.

        
Si je veux faire une verif par mail lors de l'inscription sur le site, est-ce que je peux : 

lors du signup, creer un nombre de 6 chiffres aleatoire, le stocker dans un champ "code" dans la table user
dans la table user, avoir aussi un champ "compteVerifie", qui est un booleen, à false
envoyer le code par mail
rediriger vers une page disant : merci de rentrer le code que nous venons de vous envoyer par mail

depuis le code rentré dans l'input de cette page, comparer avec le code en base. 
Si c'est le meme code, passer le booleen "compteVerifie" à True ?

Mettre en place le mot de passe oublié également

utiliser @JsonIgnore pour ne pas envoyer le mot de passe dans le front ?

Pour les pages accessibles à n'importe qui, ne jamais envoyer le token depuis Redux,
et n'appeler que des routes qui commencent par /visitor

Pour les pages accessibles aux utilisateurs connectés, envoyer le token depuis Redux,
et n'appeler que des routes qui commencent par /visitor et /user

Pour les pages accessibles à l'administrateur, envoyer le token depuis Redux,
et n'appeler que des routes qui commencent par /visitor et /user et /admin

Le token est rempli d'information qui me semble important de voir figurer dans le Token (username et role)

dans le front tout est pret pour avoir un crud hyper fonctionnel sur les tables
tout est pret egalement pour afficher ou non des choses selon le role de l'utilisateur
tout est pret pour travailler du css hyper precisement et a ma facon (faire du scss dans chaque component)

commencer à regarder du cote de docker

cours sql de Grafikart : voir les vues, les triggers et les requetes recursives

parler des champs de la table user qui ont changé de nom, car je voulais respecter la gestion de JWT avec spring (champ username qui est verifié etc...)

la table de joinutre users_roles a disparu car elle n'etait pas pertinente, finalement c'est un champs role dan sla table user qui est bien sur la plupart du temps à role : USER

depuis react, et le front end en general, il est impossible d'obtenir le path complet d'un fichier lors d'un input type="file"
pour des raisons de securite, on obitne toujours C:\fakepath\image.jpg

Le but est donc simplement d'upload le file, pas d'en connaitre le chemin complet

En java, je dois également comprendre comment passer du multipartfile reçu, à l'instertion en base du fichier avec le type mediumblob.
Probablement le FileSystemStorageService à revoir car lui il stocke dans un dossier predéfini par moi-même, et pas en base

installer sonarlint

1 seule table file, 
car on retrouve les medias en faisant des get sur les entites
en revanche ils era compliqué depuis la table files de savoir quel media appartient a quelle entite (une categorie ? un user ?)
mais ce get sur les files n'arrivera jamais

faire un dockerfile pour deployer l'API Java Spring
build,
créer le jar
executer le java -jar

maquette


g


il s'agit ici de verifier que l'heure d'expiration du token est bien postèrieure à l'heure actuelle, 

je fais ça direcement dans app.js pour que cette vérif se fasse tout au long de l'app


edit : ce n'est pas possible, la page APP et le componant app.js n'ont pas vraiment de vue donc impssible d'utiliser les lifecycle method d'Ionic.

mais pas securité j'apprends également à implement la fin de cette verification piur ne pas qu'elle s'execute à l'infini
(dans le cas ou je fais une autre verification dans un composant qui a une duree de vie limlité)

parler de la fonction componentDidMount() componentWillUnmount() 
qui sont sont finalement utilisés comme ça dans le useffect : 
    useEffect(() => {
        // Anything in here is fired on component mount.
        return () => {
            // Anything in here is fired on component unmount.
        }
    }, [])

    https://robertmarshall.dev/blog/componentwillunmount-functional-components-react/

    mais ce useffect a un probleme, il fonctionne avec un router de ce genre (v5.2.0) : 
        <BrowserRouter>
      <Header />
      <Switch>
        <Route path="/" component={HomePage} exact />
        <Route path="/contact" component={ContactPage} />
      </Switch>
    </BrowserRouter>
    https://www.freecodecamp.org/news/common-mistakes-react-developers-make-and-how-to-fix-them/

    or moi avec ionic j'ai ce genre de router : 
     <IonRouterOutlet id="main">
            <Route exact path="/accueil">
              <Accueil />
            </Route>
            <Route exact path="/categories">
              <Categories />
            </Route>
            <Route exact path="/categorie/:id">
              <Categorie />
            </Route>
            <Route exact path="/">
              <Redirect to="/accueil" />
            </Route>
    </IonRouterOutlet>

https://forum.ionicframework.com/t/ionrouteroutlet/189545

donc Ionic ne fais jamais de unmount à ses composants : donc il faut utiliser leur fonction (lifecycle methods): 
https://ionicframework.com/docs/react/lifecycle

 ionViewWillEnter() {
    console.log('ionViewWillEnter event fired');
  }

  ionViewWillLeave() {
    console.log('ionViewWillLeave event fired');
  }

  ionViewDidEnter() {
    console.log('ionViewDidEnter event fired');
  }

  ionViewDidLeave() {
    console.log('ionViewDidLeave event fired');
  }

  donc pour la suite de développement front je n'utiliserai plus use effect car me concenrant il ne s'executera qu'au premier affichage du composant

  https://programmingwithswift.com/how-to-compare-dates-with-typescript/
  pour compaerer deux dates, en JS avec des format ISO

  utilisation  de sonarlint, comparer le code de 2009 d'APRR et le mien sur le projet

  utilisation et configuration de prettier rc pour format on save


  Pour les tests, en profiter pour montrer ma collection postman complète, ainsi que celle de YouTube et du FileUpload.

  Lors d'une integration continue, les tests sont executés très régulièrement donc on est au courant dès qu'une fonction ne fait plus son travail.

  le role de mockMvc est d'executer les requetes appel API

  jUnit donne la fonction assert, pour vérifier les retours de ces appels

  avoir une classe RestTestConfiguration pour configurer les executions des requetes

  exporter avec electron pour une version desktop par exemple, pour profiter des performances de l'os plutot que du navigateur, et acceder aux ports usb de l'ordinateur par exemple etc...
  les applis pure desktop ne sont plus trop la norme, on a à faire à des applis web portées en desktop désormais

  c8, utilité des trigger,
  monitoring des actions effectués
  dans interop, les sequences,
  dans recouvrement les actions effectuées
  ce que fait le dba lorsqu'il crée les triggers vu depuis dBeaver

  UsersRoles en java

  cours de graphikart sur le sql, les vues et triggers
  pouvoir expliquer ce qu'est une vue et un trigger

  c10; user story
  use case
  definitions des specifications fonctionnelles

  C13 : de l'hybride, du responsive
  a integrer facilement dans electron et capacitor, l'equivalent d'un navigateur avec notre appli web dedans
  peut-etre parler de mon essai sur flutter, avec xcode et android studio, et l'emulateur de l'iphone (mais mon macbook air n'est pas assez performant pour ça)

  comment déployer une appli sur un store ?

  pour les tests, commencer par un test simple avant d'etoffer

  sauvega rde de base de données, cronjob
  Cron est un programme utilitaire permettant de répéter des tâches à un moment ultérieur. Donner une commande qui planifie une tâche, à un moment précis, de manière répétitive est une tâche cron.

  justifier le choix de telle ou telle base de données
  pourquoi MySQL

propriete d'atomicite, comment assurer que la transaction se fait en entier ou pas du tout
transaction, ensemble d'operation

regarder la formation SQL de Grafikart avant le passage du titre

Propriété ACID (atomicité, cohérence, isolation, durabilité) des bases de données
ça s'implémente avec des transaction

noter quand meme les differences entre mySQL, NoSQL, MongoDB etc...

faille XSS
    {{ username }}

    const username = "<script>alert('coucou')</script>"

    au li'eu d'executer le script, Vue ou React affichera en dur <script>alert('coucou')</script> au lieu d'executer le script
    géré par les frameworks JS

    possibilité d'echapper pour utiliser les entités HTML de manière forcée


faille SQL
  instertion de code au lieu d'un username
  username : '; DELETE * FROM user;

  requete SQL finale : 
  SELECT * FROM user WHERE username = :username
  transformée en 
    SELECT * FROM user WHERE username = ''; DELETE * FROM user;
    géré par l'ORM, JPA

    https://stackoverflow.com/questions/73617743/is-springboot-data-jpa-repository-safe-against-sql-injection
avoir @Query et @Param

mauvaise pratique : utiliser la simple concatenation pour construire la requete
https://stackoverflow.com/questions/3441193/are-sql-injection-attacks-possible-in-jpa

String sql = "SELECT u FROM User u WHERE id=" + id;

encore une meilleure maniere, laisser une classe construire la requete elle-même
https://www.adam-bien.com/roller/abien/entry/preventing_injection_in_jpa_query

EntityQuery query = new EntityQuery.SELECT().ENTITY().FROM(User.class).WHERE().attribute("username").build();

pour ici, prendre des exemples des NamedQueries d'APRR, avec les getResultList et getSingleResult etc...

Test : selenium IDE, extensions chrome


## Mise à jour le 14/04/22

Cette semaine voici où en est le projet : 

-  ### API
    - J'ai mis en place des tests unitaires sur mes principales routes, désormais je sais coder des scénarios à v"rifier dans l'API
    avec ou sans authentification
- ### Front-end
    - rien de nouveau
    - je dois mettre en place des tests, pour tester les formulaires et la connexion par exemple
    
- ### Conception
    - Maquettes terminées et présentables, avec benchmark

    Matrice valeur complexité

    test avec jest en react, impossible de tester des functions qui sont dans les composant,s je dois sortir les functions de composant et les expoerter seules pour pouvoir les tester.
    j'ai réussi a tester des fonctions qui se trouvent dans un composants fonctionnels, mais pas la presence ou non des IonAlert, donc je vérifier des return qui vont avec ces alertes.
    Je peux vérifier que des composants s'affichent sans faire planter l'appli, vérifier la presence d'un H1 contenant une certaine chaine de caractere. et je sais aussi vérifier qu'un input vide renvoie bien une erreur, comme prévu

    # Conseils de Michael le 22 11 2022

    - utiliser le même projet pour plusieurs compétences
    - 
    - j'ai sous les yeux une activité type, dans les 3 exemples à mettre dedans, il faut que j'en trouve des assez riches et qui sont donc en lien avec les 5 compétences professionnelles qu'on voit là ?
par exemple,mon api de recouvrement n'a rien a faire ici, n'ayant aucune interface utilisateur
par contre, mon api de RECOUV irait bien dans la 2eme activité type qui est "Concevoir et développer la persistance des données en intégrant les recommandations de sécurité"
NicolasMaes — Aujourd’hui à 16:31
 question la 2eme activite  "Concevoir et développer la persistance des données en intégrant les recommandations de sécurité" c'est axé BDD c'est ça ? une API n'a pas trop sa place dedans ? meme si mon API comporte pas mal de requete SQL et HQL ? 
reponse    - C3 JPA Hibernate

Et du coup mon travail sur les API est à mettre dans la 3eme activité type "Concevoir et développer une application multicouche répartie en intégrant les recommandations de sécurité" et en particulier les competences 
11
Développer des composants métier
12
Construire une application organisée en couches

j'ai bon ?
Michael Lhomme — Aujourd’hui à 16:35
j'ai pas pris le temps de lire encore
ok je réponds a ca en visio du soir ca ira pour tout le monde
NicolasMaes — Aujourd’hui à 16:38
ok, je continue quelques questions : les API ca irait plutot dans le C5 Développer la partie back-end d’une interface utilisateur
web non ?
et derniere question j'ai deux projet python, 1 perso sur l'extraction de meta données des videos youtube (utilisationde l'api) et un autre en entreprise ou je recevai un json que je transormai en CSV pour le remettre à disposition ailleurs (j'en faisais un .exe). 
Est-ce que ce sont des projets dont je peux parler dans le C3 Développer des composants d’accès aux données
desfois je me emts à ta place, avec toutes les sollicitations que tu dois recevoir au fil de la journée... tu dois apprécier le soir quand ça s'arrête 🙂

Les BDD doivent respecter les critères DICP : Disponibilité, Intégrité, Confidentialité et Preuve

websocket

test 
