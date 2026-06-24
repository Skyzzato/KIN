\# DOCUMENTO 5 (oppure 21) – ALGORITMO DI MATCHING KIN (BOZZA 1.0)



\## Premessa



L'algoritmo di KIN non ha lo scopo di trovare il maggior numero possibile di persone.



Ha lo scopo di individuare le migliori Occasioni.



Per questo motivo privilegia qualità e contesto rispetto alla quantità.



\---



Questo documento contiene tutte le regole decisionali del cervello di KIN.



Esempi:



quando nasce un'Occasione;

quando viene ignorata;

quando viene riproposta;

come si calcola il Valore dell'Occasione;

come si combinano Affinità, Serendipità e Vicinanza;

quali soglie usare;

come evitare notifiche ripetitive;

come gestire casi limite (GPS impreciso, utenti in auto, profili appena iscritti).



Questo documento dovrebbe essere scritto con estrema cura, perché qualsiasi sviluppatore potrebbe implementare KIN leggendo solo queste regole.



\---



🧠 core-engine



Contiene solo:



algoritmo di matching;

DNA di Affinità;

Indice di Serendipità;

calcolo del Valore dell'Occasione;

logica decisionale.



Tutto il resto gli chiede semplicemente:



Occasion occasion = coreEngine.calculate(userA, userB);



e lui risponde:



Compatibilità: 93%



Serendipità: 88%



Valore: 91%



Genera Occasione: SI



Il core-engine diventa così il vero cervello di KIN.



\---



\# Valore dell'Occasione



Ogni Occasione è identificata da un punteggio complessivo denominato:



VALORE DELL'OCCASIONE (0-100)



Il valore è determinato dalla combinazione di quattro macrofattori:



\* Affinità

\* Vicinanza

\* Serendipità

\* Disponibilità



\---



\# 1. Affinità



L'Affinità rappresenta il cuore dell'algoritmo.



È calcolata confrontando il DNA di Affinità dei due utenti.



Tra gli elementi considerati:



\* differenza di età;

\* interessi;

\* hobby;

\* musica;

\* cinema;

\* libri;

\* sport;

\* viaggi;

\* stile di vita;

\* animali;

\* valori personali;

\* attività svolte.



Ogni parametro ha un peso configurabile.



L'algoritmo potrà essere modificato nel tempo senza alterare l'architettura del sistema.



\---



\# 2. Vicinanza



La Vicinanza tiene conto della distanza stimata tra i due utenti.



La distanza non viene utilizzata con soglie rigide.



Un utente a 40 metri ha maggiore probabilità di generare un'Occasione rispetto ad uno a 900 metri, ma tutti gli altri fattori continuano ad influire sul risultato.



\---



\# 3. Indice di Serendipità



Misura l'unicità dell'incontro.



Esempi:



\* presenza temporanea in una città;

\* partecipazione allo stesso evento;

\* permanenza limitata nella zona;

\* percorsi raramente coincidenti.



Una serendipità elevata aumenta il valore complessivo dell'Occasione.



\---



\# 4. Disponibilità



Lo stato dell'utente modifica il comportamento dell'algoritmo.



Modalità disponibili:



\* Disponibile

\* Automatico

\* Invisibile



La modalità Disponibile incrementa la probabilità di essere proposta come Occasione.



La modalità Invisibile esclude completamente il profilo.



\---



\# Motivazione dell'Occasione



Ogni Occasione deve essere spiegata.



L'utente deve comprendere il motivo della proposta.



Esempio:



Compatibilità: 91%



Perché questa Occasione?



\* condividete 12 interessi;

\* ascoltate gli stessi generi musicali;

\* praticate entrambi trekking;

\* avete uno stile di vita simile.



L'algoritmo deve essere percepito come trasparente.



\---



\# Diversità controllata



KIN non deve proporre esclusivamente persone identiche.



Una piccola componente di diversità può aumentare il valore umano dell'incontro.



L'algoritmo potrà introdurre una limitata variabilità per evitare la formazione di profili eccessivamente omogenei.



\---



\# Apprendimento futuro



Nelle versioni successive, l'algoritmo potrà apprendere dai comportamenti degli utenti.



Ad esempio:



\* Occasioni ignorate;

\* Connessioni create;

\* durata delle conversazioni;

\* feedback volontari.



L'apprendimento dovrà avvenire nel rispetto della privacy e senza penalizzare gli utenti.



\---



\# Principio guida



KIN non cerca di massimizzare il numero di notifiche.



Preferisce inviare poche Occasioni, ma con un'elevata probabilità di trasformarsi in Connessioni autentiche.



La fiducia dell'utente nell'algoritmo è uno degli asset principali del progetto.



\---



1\. Niente punteggi "gonfiati"



Un 95% deve essere davvero raro.



Indicativamente:



50-60% → affinità discreta

60-75% → buona

75-85% → elevata

85-92% → molto elevata

92-100% → eccezionale (pochissimi casi)



Così quando l'utente vede un 96%, sa che è un'Occasione davvero speciale.



\---



2\. Numero massimo di Occasioni



Per preservare il valore delle notifiche, suggerirei un limite dinamico:



in zone con pochi utenti: tutte le Occasioni valide;

in zone molto popolate: solo le migliori.



L'obiettivo è evitare l'effetto "catalogo".



\---



3\. Priorità assoluta



Propongo questa gerarchia:



❤️ Affinità

⭐ Serendipità

📍 Vicinanza

🟢 Stato di disponibilità



In questo modo KIN non ti propone semplicemente la persona più vicina, ma la migliore Occasione disponibile in quel momento.



\---



Il ciclo di vita di un'Occasione



Ogni 30 secondi (valore configurabile) il Core Engine esegua questo processo:



&#x20;         Utenti online

&#x20;                │

&#x20;                ▼

&#x20;     Filtra utenti invisibili

&#x20;                │

&#x20;                ▼

&#x20;    Calcola Vicinanza geografica

&#x20;                │

&#x20;                ▼

&#x20;     Calcola DNA di Affinità

&#x20;                │

&#x20;                ▼

&#x20;   Calcola Indice di Serendipità

&#x20;                │

&#x20;                ▼

&#x20;   Applica Preferenze reciproche

&#x20;                │

&#x20;                ▼

&#x20;Calcola Valore dell'Occasione

&#x20;                │

&#x20;                ▼

&#x20;    Verifica Principi KIN

&#x20;                │

&#x20;                ▼

&#x20;Genera o non genera Occasione

&#x20;                │

&#x20;                ▼

&#x20;     Spiega il perché

&#x20;                │

&#x20;                ▼

&#x20;     Invia la notifica



\---



Concetto di soglia dinamica/adattiva



Se in una città ci sono 2.000 utenti compatibili, KIN mostra solo le migliori Occasioni.

Se in un piccolo paese ci sono 15 utenti, può abbassare leggermente la soglia.

Così l'esperienza resta sempre equilibrata.



\---



🌱 Il Principio del "Mistero Positivo"



L'algoritmo non deve essere completamente prevedibile.



Se l'utente capisce esattamente come funziona, inizierà a modificarne il comportamento per ottenere più Occasioni.



Meglio mantenere una parte del funzionamento riservata, garantendo trasparenza sul perché di una proposta ma senza rivelare tutti i meccanismi interni.



Questo preserva l'autenticità dell'esperienza e rende molto più difficile manipolare il sistema.

