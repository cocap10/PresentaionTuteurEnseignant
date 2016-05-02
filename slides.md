% title: Présentation tuteur enseignant
% subtitle: Stage de fin d'étude
% author: Martin Piegay
% thankyou: Merci !
% contact: <a href="https://twitter.com/">@Martouf42</a>
% contact: <span>github</span> <a href="http://github.com">cocap10</a>
% favicon: figures/golang.icon.png
---
title: /WhoamI : Martin Piegay

<img src=figures/telecom.jpg /> 
 
 FI3 en parcours 9 :
  
  - Informatique et réseau
 
 En stage à l'agence Lyonnaise de Zenika depuis Mars 
 
---
title: Zenika

<img src=figures/zenika.png />
 
Cabinet de conseil, réalisation, formation informatique spécialisé dans l'Open Source et l'agilité. 

Siège social de l’entreprise à Paris 

Agences : Lyon, Rennes, Nantes, Lille et Bordeaux

---
title: Emile Vauge

Emile est un ancien Consultant & Formateur Zenika <img src=figures/zenika.icon.jpg />

Il est certifié Docker formateur <img src=figures/docker.icon.png />

Depuis Septembre 2015 il développe le Reverse-proxy/Load-balancer Traefik en Go

En Février 2016, il a quitté Zenika pour monter la zStartup <a href="https://containo.us/">Containous</a> <img src=figures/containous.icon.png />

Il se consacre exclusivement au développement de  <a href="https://traefik.io/">Træfik</a> <img src=figures/traefik.icon.png />

---
title: Reverse-proxy 

Permet à un utilisateur d'Internet d'accéder à des serveurs internes :

<img src=figures/Reverse_proxy.png />

---
title: Architecture Microservices 
class: img-top-center

<img height=500 src=figures/traditionnalArchitecture.png />
---
title: Træfik
class: img-top-center

<img height=500 src=figures/traefikArchitecture.svg />
---
title: Go lang

Langage open source crée en 2010 par Google

Syntaxe simple et efficace :

<pre class="prettyprint" data-lang="go">
func main(){
  fmt.Println("Hello, 世界")
}
</pre>

Compilation de 80 % à 90 % plus rapide que en C

Tout les dépendances sont intégrées dans le binaire

Février 2016 : Version 1.6

Août 2016 : Version 1.7
---

title: Structure de configuration : exemple

<pre class="prettyprint" data-lang="go">
type Configuration struct {
    Name     string       
    LogLevel string 
    Timeout  time.Duration
    Db       *DatabaseInfo
    Owner    *OwnerInfo
}
//Sub-structures DatabaseInfo & OwnerInfo are defined below
</pre>

---
title: Flæg

Une librairie pour le langage <a href="https://golang.org/">Go</a> <img src=figures/golang.icon.png />
 
Génère une interface en ligne de commande <img src=figures/cli.icon.png />

Initialise la structure de configuration avec les arguments

C'est open source, sur <a href="http://github.com/containous/flaeg">github</a> :)

---
title: Flæg : exemple 

<pre class="prettyprint" data-lang="go">
//Configuration is a struct which contains all differents type to field
//using parsers on string, time.Duration, pointer, bool, int, int64, time.Time, float64
type Configuration struct {
    Name     string        //no description struct tag, it will not be flaged
    LogLevel string        `short:"l" description:"Log level"`
    Timeout  time.Duration `description:"Timeout duration"`
    Db       *DatabaseInfo `description:"Enable database"`
    Owner    *OwnerInfo    `description:"Enable Owner description"`
}
//Sub-structures DatabaseInfo & OwnerInfo are defined below
</pre>
---
title: Flæg : exemple suite

<pre class="prettyprint" data-lang="shell">
$ flaegdemo -h
flaegdemo is a golang programme....(here the programme description)

Usage: flaegdemo [--flag=flag_argument] [-f[flag_argument]] ...     set flag_argument
   or: flaegdemo [--flag[=true|false| ]] [-f[true|false| ]] ...   

Flags:
    --db                      Enable database (default "false")
    --db.comax                Number max of connections on database (default "3200000000")
    --db.connectionmax64      Number max of connections on database (default "6400000000000000000")
    --db.ip                   Server ip address (default "192.168.1.2")
    --db.load                 Server load (default "32")
    --db.load64               Server load (default "64")
    --db.watch                Watch device (default "true")
    -l, --loglevel            Log level (default "DEBUG")
    --owner                   Enable Owner description (default "true")
    --owner.dob               Owner date of birth (default "1993-09-12 07:32:00 +0000 UTC")
    --owner.name              Owner name (default "true")
    --owner.rate              Owner rate (default "0.999")
    --owner.servers           Owner Server (default "[]")
    --timeout                 Timeout duration (default "1s")
    -h, -help                 Print Help (this message) and exit
</pre>
---
title: Stært

Une autre librairie pour le langage <a href="https://golang.org/">Go</a> <img src=figures/golang.icon.png />

Permet de fusionner les sources de configuration

Pour l’instant deux sources : 
Fleag 
Fichier de configuration (TOML)
En développement : 
Des bases de donnés Key-Value 
---
title: Træfik avant
class: img-top-center

<img height=500 src=figures/traefikOldCli.png />
---
title: Utilisation Stært & Flæg dans Træfik 
class: img-top-center

<a href="https://github.com/containous/traefik/blob/master/configuration.go"><img height=500 src=figures/traefikFlaegCli.png /></a>

---
title: Démo
