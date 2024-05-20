# Linux

> **Va rugam sa retineti ca suportul pentru sistemele Linux este limitat si poate varia drastic in functie de distributie. Pasii descrisi mai jos se aplica unei mari varietati de sisteme si sunt, in general, cei mai portabili. Daca aveti nevoie de asistenta cu o versiune grafica a Wireguard, va rugam sa consultati documentatia distributiei cu privire la acest aspect.**
>> Cuvintele cheie pentru cautarile ar putea include `Wireguard`, `Network Manager` si tipul de mediu desktop, cum ar fi `Gnome` sau `KDE`, spre exemplu.
# Versiuni de kernel

Wireguard pe sistemele Linux este alcatuit din doua componente: 

- Componenta kernel
	- Este responsabila pentru gestionarea efectiva a traficului dintre calculator si serverul VPN
	- Creeaza interfete de retea virtuale
	- Ruleaza, cripteaza si incapsuleaza traficul in pachete Wireguard
- Componenta de spatiu utilizator
	- Gestioneaza fisierelor de configurare reale
	- Gestioneaza starii tunelurilor
    - Gestioneaza trimiterea cheilor de criptare catre componenta kernel

In lumea Linux, Wireguard nu poate functiona fara componenta de kernel. Ca atare, trebuie sa va asigurati ca kernel-ul are modulul incorporat sau ca acesta poate fi incarcat de DKMS. 

In primul rand, va rugam sa verificati versiunea kernelului dupa cum urmeaza:

	$ uname -r
	6.2.10-arch1-1


In functie de versiunea kernel-ului, modulul ar putea fi deja incorporat in principalele distributii si, de asemenea, activat.

## Kernel-uri mai noi decat 5.6

Modulele de kernel Wireguard ar trebui sa fie prezente si probabil activate in Kernel. Este putin probabil sa fie nevoie sa faceti altceva in legatura cu acest aspect.

## Kernel-uri mai vechi de 5.6

> Anumite distributii realizeaza, de asemenea, backportul driverului Kernel pentru versiuni mai mici de 5.6, cum ar fi 5.4. Va rugam sa consultati manualul distributiei pentru aceste informatii.

Sistemele care ruleaza in prezent un Kernel mai vechi de 5.6 necesita ca modulul sa fie incarcat separat prin DKMS. Pachetul se numeste de obicei `wireguard` si ar trebui sa adune automat alte dependente necesare, cum ar fi DKMS insusi si sursele kernelului. Instalati acest pachet folosind managerul de pachete al sistemului.

# Instalare

In functie de distributia, va rugam sa instalati pachetul "wireguard-tools" folosind managerul de pachete al sistemului. Daca acest pachet nu este disponibil, incercati si numele "wireguard". Informatii mai explicite despre sistemul specific pot fi gasite [aici](https://www.wireguard.com/install).

Mutati fisierul pe care l-ati downlodat in pasul anterior in `/etc/wireguard`. Este posibil sa aveti nevoie de permisiuni `sudo` (sau `root`) pentru a face modificari in acest director. 

> Daca acest director nu exista, verificati daca ati instalat pachetele Wireguard necesare sau consultati manualul pachetului Wireguard al distributiei pentru detalii despre locul unde se afla acest director de configurare.

Verificati daca exista comenzile `wg` si `wg-quick` incercand sa le executati intr-o sesiune de terminal. Comanda `wg` nu ar trebui sa produca niciun rezultat in acest moment (acesta este comportamentul corect).

## Activare tunel

> Va rugam sa retineti ca numele fisierului **NU** trebuie sa contina caracterele punct sau subliniere. In acest caz, va rugam sa redenumiti fisierul inainte de a continua.

Luati aminte de fisierul pe care l-ati plasat in `/etc/wireguard`. Numele tunelului real este numele fisierului fara partea `.conf`. Ca utilizator `root`, sau prin intermediul `sudo`, activati tunelul folosind comanda `wg-quick`, dupa cum urmeaza:

	$ sudo wg-quick up test_wireguard
	[#] ip link add test_wireguard type wireguard
	[#] wg setconf test_wireguard /dev/fd/63
	[#] ip -4 address add 10.0.32.2/20 dev test_wireguard
	[#] ip link set mtu 1420 up dev test_wireguard
	[#] ip -4 route add 172.30.0.0/16 dev test_wireguard

## Statisticile tunelului
Comanda `wg` ar trebui sa afiseze acum tunelul si statisticile legate de acesta. Comanda poate fi executata de orice utilizator, chiar si fara `sudo`.

	$ wg
	interface: test_wireguard
	public key: gRpsDZdExmG6YPfFPVZHhkWdtBMSTCnZF8KfWdLkTlE=
	private key: (hidden)
	listening port: 48137

	peer: KkxqXijYvoAl96xgVUOwl1J8yz9f48z1/fZH0HucnkU=
	endpoint: 193.231.20.20:51831
	allowed ips: 172.30.0.0/16
	latest handshake: 21 seconds ago
	transfer: 184 B received, 1.51 KiB sent
	persistent keepalive: every 25 seconds

> VPN-ul poate parea activ, dar totusi valoarea octetilor "primiti" ramane zero. In acest caz, va rugam sa verificati conectivitatea utilizand un hotspot mobil. Este foarte probabil ca configuratia actuala a retelei sa nu permita utilizarea VPN-ului. Daca functionalitatea prin hotspot-ul mobil este confirmata, va rugam sa consultati furnizorul de internet pentru asistenta suplimentara.

## Dezactivarea tunelului

Puteti dezactiva conexiunea repetand procedura de activare, dar inlocuind `up` cu `down`, dupa cum urmeaza:

	# wg-quick down test_wireguard
	[#] ip link delete dev test_wireguard

# Automatizare

Puteti automatiza conexiunea la VPN prin activarea anumitor servicii, in functie de cadrul de initializare pe care il utilizeaza distributia.

## systemd

Pe masinile bazate pe systemd, pachetul `wireguard-tools` asigura integrarea prin intermediul unui serviciu modelat. Daca activati unul dintre aceste servicii folosind comanda `systemctl enable wg-quick@name`, acesta va fi executat automat la pornire. In consecinta, puteti, de asemenea, sa dezactivati functionalitatea inlocuind `enable` cu `disable`. Alti termeni acceptati sunt `status`, `start`, `stop`, `restart`. 

Sa luam urmatorul exemplu:

	# systemctl enable wg-quick@test-wireguard
	Created symlink /etc/systemd/system/multi-user.target.wants/wg-quick@test-wireguard.service → /usr/lib/systemd/system/wg-quick@.service.

	# systemctl disable wg-quick@test-wireguard
	Removed "/etc/systemd/system/multi-user.target.wants/wg-quick@test-wireguard.service".

> Aceste automatizari pot fi executate doar ca utilizator root. Serviciile systemd la nivel de utilizator nu vor functiona, deoarece comenzile de baza necesita acces `root`.

## openrc

In acest moment, openrc nu este acoperit de acest ghid.




