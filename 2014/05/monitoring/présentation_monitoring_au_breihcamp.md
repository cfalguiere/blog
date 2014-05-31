# Monitoring à l'heure de Devops et BigData

J'ai participé au Breizhcamp cette année avec une présentation sur le monitoring. 

Au passage merci aux organisateurs pour cette édition 2014. Les conférences sont toujours l'occasion de discussions passionnées sur les sujets les plus chaud du moment et puis c'est cool finalement de pouvoir assister à des conférences sans rien avoir à faire. Bravo aussi à l'initiative de faire un repas ouvert à tous le jeudi soir. On a ainsi pu partager les discussions passionnées des speaker diners avec d'autres passionnés.

<br>

Le but ce cette présentation est de revoir un peu nos idées reçues sur le monitoring. Même si le sujet n'est pas forcément très hype, Lean et Devops changent notre vision des mesures et les outils BigData viennent à notre secours.


La présentation se trouve [là](http://fr.slideshare.net/claude.falguiere/pres-monitoring-v2).

<div align="center" style="margin-bottom:20px">
[slideshare id=35058219&doc=pres-monitoringv2-140523152751-phpapp02&w=300]
</div>


[Sébastien Brousse](https://twitter.com/seb_brousse) a twitté sur une partie de la présentation où je fais un détour par la **matière noire**. Je pense que le rapport avec le monitoring est peu évident sans les explications que j'ai donné de vive voix et le [slide](http://www.slideshare.net/claude.falguiere/pres-monitoring-v2) ne vous sera pas forcément d'une grande aide.

Pour ceux qui n'étaient là en attendant la vidéo voici les explications et même quelques infos supplémentaires.


## Mais pourquoi la matière noire ? 


Non, je n'ai pas changé de métier, la présentation parlait bien de **monitoring**.

Tout d'abord il y a peu de **femmes dans l'informatique** et donc dans les conférences, et c'était l'occasion d'avoir deux grandes dames avec nous, [Margaret Burbidge](http://en.wikipedia.org/wiki/Margaret_Burbidge) et [Vera Rubin](http://en.wikipedia.org/wiki/Vera_Rubin), deux astrophysiciennes.

La première a imaginé **le concept de matière noire**, la seconde a poursuivi les travaux et mis au point **une méthode pour prouver son existence**. 

Nous on est n'est pas des astrophysiciens, je vais rester à un niveau assez général. Pour les détails, sur la [matière noire](http://fr.wikipedia.org/wiki/Mati%C3%A8re_noire) je vous renvoie à [Wikipedia](http://fr.wikipedia.org/wiki/Mati%C3%A8re_noire). 

## Des galaxies prises en excès de vitesse
<div style="float:left;margin-right:15px; margin-bottom:15px;margin-top:5px">
<img src="https://cfalguiere.files.wordpress.com/2014/05/pia04224_ip_web_square.jpg" style="width:150px;height:150px"/>
</div>

Cette découverte a un rapport avec le monitoring  parce que tout ça découle de **problèmes de mesure**. 

Les astronomes avait constaté depuis longtemps que les **galaxies spirales tournaient trop vite** par rapport à la **masse** qu'elles sont supposées avoir d'après les mesures. 

Plusieurs hypothèses ont été avancées pour expliquer cette bizarrerie en particulier l'imprécision des mesures.

Dans les années 1970, [Margaret Burbidge](http://en.wikipedia.org/wiki/Margaret_Burbidge) a refait les mesures avec toute la précision des moyens de l'époque. Et là, ça ne collait toujours pas. 

Plutôt que de remettre en cause les mesures, [Margaret Burbidge](http://en.wikipedia.org/wiki/Margaret_Burbidge)  a **remis en cause le raisonnenment**. Si la vitesse ne colle pas avec la masse, c'est que **la masse n'est pas celle que l'on pense**. 

A cette époque on **évalue la masse** à partir des objets que l'on peut **observer au téléscope**, donc ceux qu'on peut voir parce qu'ils émettent de la **lumière**. Par conséquent, elle en a déduit qu'il y a dans les galaxies quelque chose **qui a une masse** mais que l'on ne voit pas parce que ça **n'émet pas de lumière**. C'est le concept de **matière noire**.

<div style="float:right;margin-left:15px; margin-bottom:15px">
<img src="https://cfalguiere.files.wordpress.com/2014/05/mwart_spitzer_c42_ap050825_web_square.jpg" style="width:150px;height:150px"/>
</div>

[Vera Rubin](http://en.wikipedia.org/wiki/Vera_Rubin) qui travaillait avec Margaret Burbidge a apporté des éléments de preuve en mettant au point **une méthode de calcul de la masse** basée sur l'**influence gravitationnelle** de la galaxie sur son environnement, ce qu'on appelle la **masse dynamique**. A la différence de la masse lumineuse, la masse dynamique est **compatible avec la vitesse de rotation** des galaxie spirales. Et la masse dynamique basée directement sur l'effet de la masse n'a pas de raison d'être fausse, ce qui justifie qu'il y a un **élément non visible ayant une masse**.


## Bon, d'accord mais moi je mesure des requêtes HTTP 
<div style="float:left;margin-right:15px; margin-bottom:15px;margin-top:5px">
<img src="https://cfalguiere.files.wordpress.com/2014/05/m81loop_miller_960_ap130416_web.jpg" style="height:150px"/>
</div>

Ok, nous on ne mesure pas des galaxies, mais même si on peut parfois regarder le serveur, enfin la boîte, finalement ce qu'on mesure est tout aussi **peu visualisable**. 

Cette histoire montre que c'est important de **mesurer de la bonne manière**.

Si on mesure des **effets indirects**, on est dépendant d'un **modèle**. Ce modèle c'est l'idée qu'on se fait du fonctionnement du système et il peut être faux. 

Dans un certain nombre de cas, cette mesure indirecte marche, par exemple la masse lumineuse convient pour les objets très lumineux comme les étoiles. Mais de temps en temps, ça ne marche pas. 

Bien sûr, on n'a pas toujours la possibilité de mesurer l'effet direct, et de temps en temps on doit se baser sur une mesure indirecte parce que c'est plus **abordable**. Dans ce cas il faut rester vigilant, et savoir remettre en cause le modèle qu'on se fait du système. 


## Notre matière noire
<div align="center">
<div style="margin-bottom:15px;margin-top:15px;margin-top:5px">
<img src="https://cfalguiere.files.wordpress.com/2014/05/eso510_hst_960_web_bandeau.jpg" style="height:150px"/>
</div>
</div>


Qu'est ce que c'est **notre matière noire** à nous les informaticiens ? 

Ce sont les **caches**, les **buffers**, les **load balancers**, les **heuristiques** sur les files d'attente, les **optimisations** de JVM, tout un tas de **mécanismes internes** au système qui le rendent plus performant, mais qui font aussi que certaines de nos mesures ont un comportement erratique ou n'ont plus de sens dans certaines situations.

Au final, mesurer correctement les performances d'un système ou d'une application informatiques est une activité qui réserve toujours des **surprises**. On ne peut pas se contenter de poser des sondes au petit bonheur la chance sans comprendre ce qu'on fait. Il faut **comprendre** le système et comment il **fonctionne** pour le mesure correctement.

On a un peu plus de chances, en cas de doute on peut souvent se reporter à la **documentation** (quoique à la réflexion pas toujours) ou demander au **développeur** (enfin des fois … ).  

Mais par contre, un cache c'est **beaucoup moins beau** sur les photos qu'une **galaxie spirale**.

<div align="center">
<img src="https://cfalguiere.files.wordpress.com/2014/05/ap030310_web_square.jpg" style="margin-left:auto;
margin-right:auto;width:300px;height:300px"/>
</div>


<div style="clear:both"/>

<div style="margin-top:20px">
Les images proviennent toutes de la [galerie d'images de la Nasa](http://www.nasa.gov/multimedia/imagegallery/).
</div>
