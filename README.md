# Lo Studiolo

Una web app per studiare in due un argomento nuovo ogni mese e diventare più colti.

- **Argomento del mese**: il programma di studio diviso in 4 capitoli, uno per settimana, con libri consigliati e altre fonti: podcast, film, serie, documentari, video su YouTube e luoghi da visitare. Anche ogni settimana ha le sue fonti da ascoltare e guardare. I link portano a una ricerca su YouTube, su Google o sulla mappa, così funzionano sempre. Mostra i progressi di entrambi e la settimana in corso.
- **Settimana**: concetti chiave, letture e fonti. C'è anche un tutor a cui fare domande. Ogni settimana è divisa in 3 lezioni scritte da Claude, che restano salvate e si possono segnare come lette. Ogni lezione segue sempre questa struttura: spiegazione approfondita, contesto storico, nomi, date, istituzioni e concetti fondamentali, esempi concreti, collegamenti con altri argomenti, una mappa di riepilogo disegnata dall'app e due domande da discutere insieme.
- **Test**: ogni settimana ha il suo test conclusivo di 30 domande, uguali per entrambi. C'è poi un esame finale di 30 domande su tutto il mese. Ogni risposta ha la sua spiegazione.
- **Allenamento libero**: un test di 10 domande quando volete, che non dà punti, con domande solo sulle settimane che avete già completato, prese dai test o scritte da Claude.
- **La sfida**: si salvano tutti i punteggi. Ogni test vale un punto per chi ha il risultato migliore. Una tabella confronta i vostri record e mostra gli ultimi test.
- **Votazione**: l'argomento del mese successivo lo scegliete voi. Si propongono 5 argomenti, scritti a mano o suggeriti da Claude. Ognuno ha 3 voti da dare a 3 argomenti diversi, al massimo uno per argomento. I voti dell'altro restano nascosti finché non avete votato entrambi. Vince l'argomento con più voti. In caso di pareggio potete cambiare i voti o tirare a sorte. Il vincitore entra nel piano annuale e Claude ne prepara il programma.
- **Temi**: ogni argomento appartiene a uno di questi dieci temi: geopolitica, storia, arte, letteratura, economia, politica, scienza, filosofia, tecnologia, cultura. Claude propone solo argomenti con un tema valido. Le 5 proposte di una votazione hanno temi diversi tra loro.
- **Piano annuale**: dodici argomenti modificabili, che coprono tutti e dieci i temi. Claude prepara il programma completo del mese con un clic e può proporre alternative.
- **Archivio**: tutti i mesi studiati, con i risultati di ciascuno.

## Dove si usa

L'app è pubblicata come Artifact su claude.ai. Lì i dati si salvano in un database condiviso, così i progressi restano sincronizzati tra voi due e su tutti i dispositivi. Lì funziona anche la generazione dei contenuti con Claude. Per usarla in due, condividete l'artifact dal menu Condividi con un livello di accesso che permetta di modificare, cioè Collaboratore o superiore.

Se aprite `studiolo/index.html` direttamente nel browser, l'app funziona in modalità locale: i progressi restano solo in quel browser e Claude non è disponibile.

## Struttura

- `studiolo/index.html`: l'intera app (HTML, CSS e JavaScript, senza dipendenze né build).
- `studiolo/seed/`: i contenuti iniziali caricati nel database: il programma di ottobre 2026 (Il Rinascimento italiano, 4 settimane), il piano annuale e i test conclusivi delle settimane.

## Dati salvati

| Collezione | Documento | Contenuto |
|---|---|---|
| `topics` | `AAAA-MM` | programma del mese: capitoli, libri, extra |
| `progress` | `AAAA-MM--<utente>` | settimane completate, lezioni lette, libri letti, risultati e storico di test, allenamenti ed esame finale |
| `quizzes` | `AAAA-MM--c1` … `AAAA-MM--final` | domande dei test |
| `lessons` | `AAAA-MM--c1--l1` … `--l3` | le tre lezioni di ogni settimana, scritte da Claude |
| `plan` | `year` | piano annuale |
| `votes` | `AAAA-MM` | votazione del mese: 5 candidati, stato, vincitore |
| `ballots` | `<utente>` | voti di ciascuno; ognuno può modificare solo i propri |
