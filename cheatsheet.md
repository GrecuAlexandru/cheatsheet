# EXERCITII REZOLVATE DE MINE

Afisati toate fisierele ce contin caracterul "a"

ls | grep a


# PROCESE

## COMANDA **PS**

**ps aux**

	a = arata procesele tuturor utilizatorilor
	u = arata detinatorul procesului
	x = afiseaza procesele ce nu apartin termialului
	
### Pentru vizualizarea ierarhiei de procese (ps -H)

**ps -e -ouser,uid,pid,%mem,%cpu,rss,cmd --sort=%mem/%cpu** - afiseaza toate nebuniile despre un proces si sorteaza in functie de cat ocupa din memorie/procesor

## COMENZI

**pgrep** - "grep" pentru numele unuia sau mai multe procese (afiseaza PID)

**pidof** - afiseaza PID ul unui proces

**pstree** - "tree" pentru procese

**uptime** - afiseaza de cat timp e pornit sistemul + ora curenta + cati useri sunt logati

**fg** - pune procesul in foreground (are input de la user)

**bg** - pune procesul in background (nu mai poate lua input de la user); `comanda` & SAU `comanda` si CTRL + Z-> trimite comanda in background

**job** - arata starea procesului

**kill PID** - trimite semnal care procesul cu PID ul dat

**pkill NUME_P** - trimite semnal catre procesul cu numele dat

**killall NUME_P** - "omoara" procesele cu numele dat

# RETELISTICA SI INTERNET

**wget** - descarcarea resurselor cu suport pentru HTTPS si FTP

**curl** - descarcarea resurselor cu suport pentru IMAP, SFTP

**ssh** - folosit pentru conexiunea la distanta

**scp local_file username@hostname:path** - copiere fisiere prin ssh


# INTERFATA IN LINIA DE COMANDA
## FILTERE TEXT

**cat** - afiseaza continului unui fisier

**tac** - "cat" de jos in sus

**rev** - afiseaza liniile inversate (primul elem de pe linie devine ultimul)

**cut -d 'separator' -f indicele uneia sau mai multor coloane** - separa coloanele unui fisier si le afiseaza pe cele date dupa -f

**sort** - sorteaza intrarile

**sort -r -n** - sorteaza invers, numeric

**uniq** - elimina duplicatele (dupa ce au fost sortate)

**wc** - numara elementele

**wc -c** - numara caracterele

**wc -l** - numara liniile

## EXPRESII REGULATE
	a* = a de oricate ori (posibil niciodata)
	a+ = a de oricate ori (macar o data)
	a? = a o data sau niciodata
	^ = inceput de linie
	$ = sfarsit de linie
	[a-z] = de la a la z
	[^a-z] = orice inafara de ce e de la a la z
	. = orice
	
	[_a-zA-Z][_0-9a-zA-Z]* = nume de variabila/functie
	07[:digit:]\{8\} = numar de telefon (07 + orice alte 8 cifre)
	

# AUTOMATIZARE IN LINIA DE COMANDA

## SCRIPTING

**chmod a+x script.sh && ./script.sh** - permisiuni de executie + rulare

**#!** - (shebang) - indica interpretorul scriptului

## !! COMENZILE DE AFISARE NU SE FOLOSESC IN SCRIPTURI !!

ls, ps, df, ifconfig, w

## SE FOLOSESC COMENZI DE PRELUCRARE 

stat, find, grep, head, tail ...

## VARIABILE

	$? - codul de iesire al ultimei comenzi
	$$ - PID ul procesului curent
	$# - numarul de argumente in linia de comanda
	$1, ..., $n - argumentele
	
### IFS = input field separator
Folosit alaturi de while read in date retinute sub forma de tabel (elem1, elem2)

**for** - folosit pentru parcurgerea elementelor unei liste (ls, ps)
**while** - folsit pentru impartirea elementelor dintr o linie pe bucati

### EXEMPLU

	for i in $(ls); do echo $i; done
	
	while read i j; do echo $i $j; done (in while poti merge cu mai multe elemente, in for doar cu unul singur)
	
# GITHUB

**git init** - initiaza un folder local pt git

**git remote add origin URL** - adauga remote-ul la git ul creat local

**git clone URL** - descarca un repo pe local intr-un folder cu numele repo-ului

**git status** - arata statusul gitului local

**git add fisier** - adauga fisierul spre a fi commited

**git commit -m "Mesaj"** - commit cu un mesaj (pe local)

**git branch** - lista de branch-uri

**git branch branch_nou** - creeaza un branch

**git checkout branch** - muta pe branch ul selectat

**git branch -d** - sterge un branch

**git push origin branch** - "publica" commitul curent pe remote, pe branch ul selectat


# COMPONENTE HARDWARE

**sudo lshw** - arata informatii despre hardware

**lshw -short** - arata mai putine informatii despre hardware

**lscpu** - arata informatii despre procesor

**lsmem** - arata informatii despre memorie

**lsmod** - arata driverele

**uname -a** - arata informatii despre kernel


# UTILIZATORI

**su** - schimba utilizatorul (cere parola userului pe care te conectezi)

**sudo** - ruleaza comenzi ca root (se cere parola utilizatorului de pe care rulezi comanda) (**!!AU PERMISIUNI DE ROOT DOAR CEI DIN GRUPUL SUDO**)

## INFORMATII AFLATE IN FISIERE

	/etc/passwd - informatii despre utilizatori
	/etc/shadow - parolele utilizatorilor (criptate)
	/etc/group - informatii despre grupuri
	
## UTILITARE

	**id** - informatii despre utilizator
	**groups** - grupurile utilizatorului curent
	**users, w, who** - utilizatorii conectati in sistem
	**whoami** - numele utilizatorului curent
	**finger, pinky** - informatii despre utilizator
	
## OPERATII

	**useradd** - adauga utilizator (fara parola)
	**adduser** - adauga utilizator (cu parola)
	**userdel** - sterge utilizator
	**usermod** - modifica utilizator
	**usermod -aG grup user** - adauga utilizatorul user in grupul grup 
	**groupadd** - adauga grup
	**groupmod** - modifica grup
	**groupdel** - sterge grup
	**chsh** - modifica shell (terminal)
	**chfn** - modifica informatii utilizator
	**passwd** - schimba parola

## MODIFICARE FISIERE

	**chown** - modifica utilizatorul si grupul
	**chgrp** - modifica grupul
	**chmod** - modifica permisiunile

## PERMISIUNI

	rwxrw-r-- (userul are permisiuni de citire/scriere/executie; grupul de citire scriere; ceilalti doar de citire)
	
	**sudo chmod +r** - adauga permisiuni de citire pentru toti
	**sudo chmod u/g/o +r** - adauga permisiuni de citire pentru user/grup/others
	**sudo chmod -r** - sterge permisiunea de citire pentru toti
	**sudo chmod u/g/o -r** - sterge permisiunea de citire pentru user/grup/others
	
	Se aplica aceleasi reguli pentru permisiunile de scriere (w) si executie (x).
	
	**sudo chmod +s** (folosit pe fisierele executabile) - executa fisierul cu privilegiile userului/grupului care l a creat
	
# ADMINISTRAREA SPATIULUI DE STOCARE

	**lsblk** - arata discurile si partitiile
	
