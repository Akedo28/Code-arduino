Explication du code du thermomètre ligne par ligne
 
Ligne 1 à 10 :
Déclaration des librairies qui vont être utilisé pour ce programme et déclaration des deux écrans Grove et du multiplexeur.
 
Ligne 12 à 16 :
Activation des canaux du multiplexeur pour envoyer le flux de la carte aux écrans
Ligne 18 à 22 :
Ajout de la variable pour le clignement des yeux du smiley, c’est dans cette partie que l’on peut changer les variables du thermomètre ici la plage est de 0 à 40 degrés, la température initiale a été ajouté pour faire des tests sans thermistance.
Ligne 25 à 31 :
Création des Sprites de la barre pour crée une barre interactive qui monte et qui descend en fonction de la température.
Ligne 34 à 58 :
Création des Sprites de chacun des nombres ils vont de 0 à 9 la partie « chiffres haut » correspond à l’affichage des chiffres sur la première ligne de l’écran (ici colonne car l’écran est retourné à 90°) et « chiffre bas » correspond au chiffre du bas donc à la deuxième colonne, l’affichage de la température se fait sur deux colonnes pour plus d’esthétisme donc chaque nombre a été « coupé » en deux, et chaque moitié à été redessiné en pixel grâce à l’affichage personnalisé.
Ligne 60 à 70 
Création des sprites pour que le smiley ouvre et ferme les yeux, souris, soit normale ou triste. Seule la bouche du smiley change, les yeux reste les même avec un clignotement certes mais sans changement d’émotion. Ajouts également du symbole degré.
Ligne 78 à 99 :
Initialisation des paramètres, sélection et démarrage des écran, création de la boucle pour l’affichage de la barre et assignation sur l’écran du haut (chanel 0, ldc 2).
”for (int col = 15; col >= 0; col--)”  Cette boucle for définira le nombre de colonnes que la barre rempliera ici l’écran possède 2 colonne et 7 lignes .
“int segmentsCol = segments - (15 - col) * 4” Dit le nombre de demi-niveaux que la colonne peut affiché ici nous avons opté pour un affichage de 4 demi-niveaux pour que la colonne se remplisse de manière fluide.
 
“for (int ligne = 0; ligne < 2; ligne++)” Dette boucle nous permet d’afficher deux lignes par colone une sur la collone 0 et une autre sur la colone 1.
 
Ligne 133 à 204:
“static int tempmax = -100” Est une valeur impossible à rentrer pour effectuer le premier affichage.
“static unsigned long nouvelleinfo = 0;  const long temps = 500;”  Nouvelleinfo nous permet de savoir quand le dernier affichage à été fait, on met un delay de 500ms entre chaque affichages.
“if (t == tempmax && (millis() - nouvelleinfo < temps)) {
  return;
  }” Indique que si la int(temperature) n’a pas changé alors nous ne devons pas faire de nouvel affichage.
“int dizaine = t / 10;   int unite = t % 10;” Cette partie est cruciale car elle nous permet de séparer les dizaine et les unté du nombre reçu par la foncction temperature.
“lcd1.createChar(0, chiffreshaut[unite]);” L’affichage sera fait par cette suites de caractères personalisés à l’aide des sprites crée précédament.
Le reste du void sert à l’affichage et la partie smiley qui a déja été expliqué dans le compte rendu.
Ligne 228 à 246:
“clignement = !clignement” Permet d’inverser le boolééen clignement déffinie au tout début du programme.
 
“if (clignement) {
      lcd1.createChar(7, smileynormal);
      delay(3000);
    } else {
      lcd1.createChar(7, smileyferme);
    “
Cette partie nous sert à faire clignoter les yeux su smiley toute les 3 secondes, c’est ici que l’inversement nous sert à alterner entre la première condition du if et else.
 
Sources complémentaires non présente dans le compte rendu :
 
Problème rencontré par rapprt à la ram de l’écran (cgram): 
https://forum.arduino.cc/t/more-than-8-custom-characters-on-liquidcrystal-display/926722
