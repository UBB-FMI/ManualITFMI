# SSH & SFTP

## Informatii generale

Accesul SSH la servicii depinde de obicei de cazul de utilizare al acestora. Unele dintre ele functioneaza prin autentificare cu parola, altele necesita configurarea unei perechi de chei.

> Este puternic recomandat sa configurati un mecanism de autentificare bazat pe chei **cat mai curand posibil**, deoarece autentificarea bazata pe parole ar putea fi dezactivata si depreciata pentru serverele de mare profil.

Atat cadrele didactice, cat si studentii au acces SSH la resursele lor respective. In acest moment, serverele cadrelor didactice sunt impartite in mai multe componente:

- Serverele Departamentului de Informatica
	- `nessie.cs.ubbcluj.ro` - Numele de domeniu principal pentru cadrele didactice, rezolvat de serverele DNS interne
        - `www.cs.ubbcluj.ro` - Numele de domeniu extern, rezolvabil de peste tot
        - `cs.ubbcluj.ro` - Numele de domeniu exterior, **NU** este rezolvat local
		- `172.30.0.3` - Adresa IP interna directa. _Aceasta adresa ar putea fi in curand interzisa pentru public._
	- `linux.scs.ubbcluj.ro` - Numele de domeniu principal pentru studenti, rezolvat de serverele DNS interne
        - `www.scs.ubbcluj.ro` - Numele de domeniu extern, rezolvabil de peste tot
        - `scs.ubbcluj.ro` - Numele de domeniu exterior, **NU** este rezolvat local
		- `172.30.0.4` - Adresa IP interna directa. _Aceasta adresa ar putea fi in curand interzisa pentru public_.
- Serverele Departamentului de Matematica
	- `math.ubbcluj.ro` - Numele de domeniu principal pentru profesori, rezolvat peste tot
		- `172.30.0.5` - Adresa IP interna directa. _Aceasta adresa ar putea fi in curand interzisa pentru public_.
- Serverele Liniei Maghiare 
    - **_In prezent in curs de documentare._**

## Porturi

Puteti accesa serviciile SSH de pe aceste servere (adresa poate fi inlocuita in functie de datele de mai sus) la diferite porturi, enumerate mai jos:

| Server                 | Port     	|
|------------------------|--------------|
| `nessie.cs.ubbcluj.ro` | **2222** 	|
| `math.ubbcluj.ro`      | **2222** 	|
| `linux.scs.ubbcluj.ro` | **22**   	|

## Servicii

Toate serverele ofera un shell, precum si servicii SFTP pentru actualizarea fisierelor din directorul personal.

> SFTP este modalitatea recomandata de gestionare a fisierelor de pe site-ul personal. Alte metode **vor fi depreciate** in curand.

## Conectivitate

> Puteti accesa intotdeauna aceste servere prin intermediul unei conexiuni VPN privilegiate. Pentru unele dintre aceste servicii, accesul este permis de la distanta fara utilizarea unui VPN. Cu toate acestea, trebuie sa solicitati mai intai permisiunea, precum si sa cereti echipei IT sa va configureze un whitelist.

In functie de sistemul de operare, exista mai multe modalitati de conectare. Va rugam sa consultati ghidurile fiecarui sistem de operare in parte.

## Raspundere

Va rugam sa retineti ca sunteti unic responsabil pentru actiunile efectuate in numele dumneavoastra pe serverele noastre.

> Va rugam sa retineti ca utilizarea unei perechi de chei criptografice va ofera un fisier de identitate, pe baza caruia serverele stiu cine sunteti si va acorda acces. Este responsabilitatea dumneavoastra de a va asigura ca acest fisier nu este furat, deoarece acest lucru poate duce la posibilitatea ca alte persoane sa se dea drept dumneavoastra. Va rugam sa fiti atenti la practicile din ghid privind stabilirea unei parole pentru perechea de chei. 