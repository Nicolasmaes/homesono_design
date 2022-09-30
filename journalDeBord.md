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
        websocket
        demander a michael si le jour j on presente l'appli dans l'etat ? 
        On peut faire une demo rapide de l'app
        Le jury a une grille de compétences à cocher donc essayer de toutes les couvrir
        Une demo de l'app peut faire perdre du temps dans la présentation
        Ajouter des captures d'écrans du code d'APRR et des apps APRR sur lesquelles j'ai travaillé
Jenkins etc...

avoir des notes de powerpoint pendant la diffusion
        puis-je utiliser notion pour presenter des trucs ?
        ou doit-on rester dans la trame de notre rapport et le suivre ? OUI

        Parler de react qui s'occupe d'empecher les injections de code dans les input

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

depuis le code rentré dans l'input de cette page,  comparer avec le code en base. 
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

En java, je dois également comprnedre comment passer du multipartfile reçu, à l'instertion en base du fichier avec le type mediumblob.
Probablement le FileSystemStorageService à revoir car lui il stocke dans un dossier predéfini par moi-même, et pas en base

installer sonarlint

1 seule table file, 
cat on retrouve les medias en faisant des get sur els entites
en revanche ils era compliqué depuis la table files de savoir quel media appartient a quelle entite (une categorie ? un user ?)
mais ce get sur les files n'arrivera jamais

faire un dockerfile pour deployer l'API Java Spring
build,
créer le jar
executer le java -jar

maquette

test 

Réesseayer de faire marcher la modal sans typescript, sans les types


on se passe donc de la foction whoami() dans le back

generer l'API dans le java directement

a implementer encore

decoder le token dans le front, c'est fait 

il s'agit ici de verifier que l'heure d'expiration du token est bien postèrieure à l'heure actuelle, 

je fais ça direcement dans app. js pour que cette vérif se fasse tout au long de l'app


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