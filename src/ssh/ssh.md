# SSH

## General Information

SSH access to serves typically depends on their use case. Some of them work by password authentication, others require setting up a keypair.

> It is highly recommended that you set up a key based authentication mechanism **as soon as possible**, because password based authentication might be disabled and deprecated for high-profile servers.

Teachers and Students alike have SSH access to their respective resources. At the moment, the Teacher's servers are divided into multiple components:

- Servers of the Department of Computer Science
	- `nessie.cs.ubbcluj.ro` - The main domain name for Teachers, resolved by internal DNS servers
		- `www.cs.ubbcluj.ro` - The outside domain name, resolvable everywhere
		- `cs.ubbcluj.ro` - The outside domain name, **NOT** resolved locally
		- `172.30.0.3` - The direct internal IP address. _This address might soon be forbidden for public use._
	- `linux.scs.ubbcluj.ro` - The main domain name for Students, resolved by internal DNS servers
		- `www.scs.ubbcluj.ro` - The outside domain name, resolvable everywhere
		- `scs.ubbcluj.ro` - The outside domain name, **NOT** resolved locally
		- `172.30.0.4` - The direct internal IP address. _This address might soon be forbidden for public_
- Servers of the Department of Mathematics
	-  `math.ubbcluj.ro` - The main domain name for Teachers, resolved everywhere
- Servers of the Hungarian Line of Teaching
	-  **_Currently pending documentation._**

> You can always access these servers by means of a privileged VPN connection. For some of these servies, access is permitted remotely without the use of a VPN.

## Ports

You can reach the SSH service on these servers at various ports, as listed below:

| Server                 	| Port     	|
|------------------------	|----------	|
| `nessie.cs.ubbcluj.ro` 	| **2222** 	|
| `linux.scs.ubbcluj.ro` 	| **22**   	|
| `math.ubbcluj.ro`      	| **2222** 	|

## Services

All servers offer a login shell, as well as SFTP services for updating files in your personal directory.