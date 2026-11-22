LA MIA AGENDA — Scuola e Coro

Pubblica tutti e quattro i file nella stessa cartella del tuo repository GitHub Pages:
- index.html
- manifest.webmanifest
- sw.js
- icon.svg

Apri l'indirizzo GitHub Pages corrispondente. I dati vengono conservati localmente nel browser.
Per utilizzare la sincronizzazione automatica tra Mac, Android e iPad, crea un progetto Firebase Spark.
Abilita Authentication con Google e Firestore Database. In Authentication > Settings > Authorized domains
aggiungi il dominio del tuo GitHub Pages (esempio: nomeutente.github.io).

REGOLE DI SICUREZZA FIRESTORE (prima di caricare dati):
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /agendas/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}

Copia il blocco firebaseConfig dalle impostazioni Web App del tuo progetto Firebase e incollalo
in Agenda > Impostazioni. Usa lo stesso account Google su tutti i dispositivi.

IMPORTANTE: App prototipo; prima di effettuare importazioni, cancellazioni o cambiare cloud
esporta un backup JSON. In caso di modifiche contemporanee da più dispositivi,
verifica quale versione conservare. Non memorizzare informazioni che identificano gli alunni.

VERSIONE 1.1 — NOVITÀ
- Archivio obiettivi didattici: pulsante "Obiettivi" in alto. Ogni disciplina ha i suoi obiettivi preimpostabili; il menu nella scheda li inserisce nel campo obiettivo, che resta modificabile.
- Colori per disciplina nei riquadri scolastici: italiano rosa, musica giallo, inglese bianco, tecnologia arancione, storia viola, matematica blu, scienze verde, geografia marrone, arte rosso.
- Orario facoltativo di inizio/fine delle singole attività.
- Scelta tra 6 caratteri tipografici in Impostazioni.
- Grassetto, corsivo e sottolineato applicabili al titolo del riquadro. Il bottone Normale azzera gli stili.
- Campo Consegne separato dalla descrizione dell'attività, incluso nell'export Word.
- Educazione motoria/fisica rimossa dall'elenco delle discipline selezionabili.

AGGIORNAMENTO: sostituire index.html e sw.js nella medesima cartella GitHub Pages. Gli altri file possono restare.
L'app usa ancora la stessa chiave di archivio locale e conserva i dati della versione precedente. Eseguire comunque un backup JSON prima di aggiornare.
La sincronizzazione tra dispositivi richiede sempre una configurazione valida di Firebase; non è automatica con il solo caricamento dei file.
\nVERSIONE 1.2.3\n- Nessuna disciplina casuale preinserita nella nuova installazione.\n- Prima creazione: chiede di impostare la settimana tipo, con scelta di continuare senza.\n- Settimana tipo: modifica con aggiunta/rimozione e salvataggio esplicito.\n- Ogni attività della giornata ha una × per rimuoverla solo dalla settimana corrente.\n- Gli archivi precedenti rimangono compatibili; i vecchi esempi non modificati vengono ignorati.\n