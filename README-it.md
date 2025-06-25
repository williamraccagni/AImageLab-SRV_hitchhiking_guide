# AImageLab-SRV: guida per autostoppisti

> [!NOTE]
> For English language: [[README]]
## Cos'è AImageLab-SRV(?)

La piattaforma AImageLab-SRV è un sistema HPC messo a disposizione dell' AImageLab a scopo di ricerca.

## Prima volta: cosa faccio?

Per prima cosa è necessario essere in possesso di credenziali per accedere alla piattaforma. Le credenziali sono fornite (in genere via mail) dopo che il vostro responsabile abbia creato l'utenza all'interno del sistema.

Le credenziali saranno del tipo:
- username 
- password

Dopo aver ricevuto le credenziali, verrà anche mandata una mail di benvenuto con una serie di Istruzioni per i nuovi utenti. Di seguito un riassunto degli stessi:
### Accesso

Per effettuare il primo accesso, è possibile effettuare una connessione `ssh` a `ailb-login-02.ing.unimore.it` o `ailb-login-03.ing.unimore.it` da un indirizzo IP dell'Università (rete via cavo, WiFi, VPN).

Screen del primo accesso:
```
    _   _                     _         _        ___ _____   __
   /_\ (_)_ __  __ _ __ _ ___| |   __ _| |__ ___/ __| _ \ \ / /
  / _ \| | '  \/ _` / _` / -_) |__/ _` | '_ \___\__ \   /\ V /
 /_/ \_\_|_|_|_\__,_\__, \___|____\__,_|_.__/   |___/_|_\ \_/
                    |___/
*********************************************************************************
* Welcome to the AImageLab HPC Platform!                                        *
*                                                                               *
* 63 GPUs, 3.3TB RAM                                                            *
* Disk Space: 0.61PB                                                            *
* SLURM 24.05                                                                   *
*                                                                               *
* Resource management and documentation:                                        *
* https://ailb-web.ing.unimore.it                                               *
* Help desk:                                                                    *
* aimagelab-srv-support@unimore.it                                              *
*                                                                               *
*********************************************************************************
* This system is in its complete configuration and is in full-production        *
=================================================================================
```

Se si dispone di un account UNIMORE, la password sarà la stessa del proprio account UNIMORE (ad esempio, quella utilizzata per ESSE3). In caso contrario, riceverete una password unica via e-mail e vi verrà chiesto di cambiarla al primo accesso.

Dopo il primo login, l'accesso è consentito attraverso le seguenti modalità:
- tramite password, quando si accede da un indirizzo IP dell'Università
- tramite una chiave SSH, da qualsiasi parte del mondo. Per aggiungere o modificare la propria chiave pubblica, utilizzare il comando `ssh-ldap-pubkey`.

Consiglio: Per accedere da esterno, invece che utilizzare il comando `ssh-ldap-pubkey` è possibile utilizzare la VPN di UniMoRe e configurarla alla seguente pagina: [Qui](https://www.sirs.unimore.it/site/home/servizi/accesso-vpn.html) 
### Storage

Lo storage di AImageLab-SRV è condiviso tra tutti i nodi. Ci sono tre posizioni che si possono utilizzare:
- `/homes/<username>`, area personale e resistente che dovrebbe essere utilizzata per memorizzare codice, registri (logs) e dati vitali
- `/work/<project>`, area a livello di progetto e ad alta capacità che dovrebbe essere utilizzata per memorizzare i set di dati e i checkpoint.

Le quote possono essere attive su tutte le posizioni. In particolare, la cartella `home` ha una quota di 100 GB. Per controllare l'utilizzo, la quota e le posizioni attive, eseguire `squota` dal nodo di accesso.

Per visualizzare i progetti a cui si è assegnati, collegarsi a: https://ailb-web.ing.unimore.it/coldfront/.
### Software

I pacchetti Ubuntu di base sono installati su tutti i nodi. Nuovi pacchetti Python e binari possono essere installati creando nuovi ambienti conda o tramite `pip install --user`.

È inoltre possibile passare da una versione all'altra dei moduli dell'ambiente (CUDA incluso) utilizzando `module load`. Si veda l'output di `module avail` per un elenco completo.

## Setting up su Visual Studio Code

Se si utilizza Visual Studio Code come code editor risulterà particolarmente utile utilizzare i pacchetti di "Remote Development" messi a disposizione da Visual Studio Code per utilizzare la piattaforma.

Guida ufficiale di Visual Studio Code: [Qui](https://code.visualstudio.com/docs/remote/ssh) 

Per prima cosa assicurarsi che nelle estensioni sia installato il pacchetto "Remote Development" in Extensions:

![[remote_development.png]]

In Remote Explorer premere sul `+` in SSH:

![[ssh_plus.png]]

A questo punto ci verrà chiesto di inserire il comando ssh seguito dalla locazione del server:

![[ask_ssh.png]]

Inseriamo `ssh wraccagni@ailb-login-02.ing.unimore.it` (o `ssh wraccagni@ailb-login-03.ing.unimore.it`). Infine selezionare il file config da aggiornare.

Eventualmente,  ripetere il processo per l'altro nodo non inserito (02 se inserito 03 o viceversa).

Per allacciarsi tramite SSH premere il tasto freccia `->` sulla voce creata precedentemente. Appena premuto ci chiederà solo la prima volta quale sia il sistema operativo della piattaforma a cui ci stiamo collegando, scegliere quindi Linux. Inserire poi la password del proprio account.

A questo punto siamo collegati in remoto con la macchina scelta.

In `Explorer` possiamo ora aprire una cartella della macchina remota e lavorare sulla macchina stessa. 

## SLURM

Se lavori con il sistema HPC del lab avrai a che fare con SLURM. **SLURM** (Simple Linux Utility for Resource Management) è un _job scheduler_ open source usato per gestire e pianificare l'esecuzione di lavori (job) su **sistemi di calcolo ad alte prestazioni (HPC)**, come cluster di supercomputer.

Per farla in breve si occupa di:

- Allocare risorse (CPU, memoria, nodi) per i job.    
- Pianificare l'esecuzione dei job in base a priorità e disponibilità.    
- Monitorare e gestire lo stato dei job.

Imparare ad usare SLURM sarà molto utile per sfruttare al meglio le potenzialità del cluster.
Qui la documentazione ufficiale per approfondire oltre ciò che questa repo ha da offrire: https://slurm.schedmd.com/documentation.html

### Alcuni Comandi utili

A seguire una serie di comandi e più usati fin dai primi istanti di utilizzo di SLURM. 
### SBATCH



### SRUN

TO DO
## TMUX

TO DO