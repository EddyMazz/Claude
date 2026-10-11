# Lo Studiolo

Una web app per studiare in due un argomento nuovo ogni mese e diventare più colti.

- **Mese in corso**: il programma del mese con 8 capitoli, libri consigliati, film e luoghi da visitare. Mostra anche i progressi di entrambi.
- **Capitolo**: concetti chiave e letture. C'è una lezione scritta da Claude, che resta salvata, e un tutor a cui fare domande.
- **Test**: un quiz a scelta multipla per ogni capitolo e un esame finale. Ogni risposta ha la sua spiegazione. Si salvano il punteggio migliore e lo storico dei tentativi.
- **Votazione**: l'argomento del mese successivo lo scegliete voi. Si propongono 5 argomenti, scritti a mano o suggeriti da Claude. Ognuno ha 3 voti da dare a 3 argomenti diversi, al massimo uno per argomento. I voti dell'altro restano nascosti finché non avete votato entrambi. Vince l'argomento con più voti. In caso di pareggio potete cambiare i voti o tirare a sorte. Il vincitore entra nel piano annuale e Claude ne prepara il programma.
- **Temi**: ogni argomento appartiene a uno di questi dieci temi: geopolitica, storia, arte, letteratura, economia, politica, scienza, filosofia, tecnologia, cultura. Claude propone solo argomenti con un tema valido. Le 5 proposte di una votazione hanno temi diversi tra loro.
- **Piano annuale**: dodici argomenti modificabili, che coprono tutti e dieci i temi. Claude prepara il programma completo del mese con un clic e può proporre alternative.
- **Archivio**: tutti i mesi studiati, con i risultati di ciascuno.

## Dove si usa

L'app è pubblicata come Artifact su claude.ai. Lì i dati si salvano in un database condiviso, così i progressi restano sincronizzati tra voi due e su tutti i dispositivi. Lì funziona anche la generazione dei contenuti con Claude. Per usarla in due, condividete l'artifact dal menu Condividi con un livello di accesso che permetta di modificare, cioè Collaboratore o superiore.

Se aprite `studiolo/index.html` direttamente nel browser, l'app funziona in modalità locale: i progressi restano solo in quel browser e Claude non è disponibile.

## Struttura

- `studiolo/index.html`: l'intera app (HTML, CSS e JavaScript, senza dipendenze né build).
- `studiolo/seed/`: i contenuti iniziali caricati nel database: il programma di ottobre 2026 (Il Rinascimento italiano), il piano annuale e i test dei capitoli.

## Dati salvati

| Collezione | Documento | Contenuto |
|---|---|---|
| `topics` | `AAAA-MM` | programma del mese: capitoli, libri, extra |
| `progress` | `AAAA-MM--<utente>` | capitoli studiati, libri letti, risultati dei test |
| `quizzes` | `AAAA-MM--c1` … `AAAA-MM--final` | domande dei test |
| `lessons` | `AAAA-MM--c1` … | lezioni scritte da Claude |
| `plan` | `year` | piano annuale |
| `votes` | `AAAA-MM` | votazione del mese: 5 candidati, stato, vincitore |
| `ballots` | `<utente>` | voti di ciascuno; ognuno può modificare solo i propri |
