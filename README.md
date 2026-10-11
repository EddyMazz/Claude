# DoubleMind

Una web app per studiare in due (Luca e Camilla) un argomento nuovo ogni mese e diventare più colti.

- **Argomento del mese**: il programma di studio diviso in 4 capitoli, uno per settimana, più 10 approfondimenti su aspetti che le lezioni non coprono (Claude li scrive su richiesta, con mappa di riepilogo). Mostra i progressi di entrambi, la settimana in corso e il tabellone della sfida.
- **Settimana**: concetti chiave. C'è anche un tutor a cui fare domande. Ogni settimana è divisa in 3 lezioni scritte da Claude, che restano salvate e si possono segnare come lette. Ogni lezione segue sempre questa struttura: spiegazione approfondita, contesto storico, nomi, date, istituzioni e concetti fondamentali, esempi concreti, collegamenti con altri argomenti, una mappa di riepilogo disegnata dall'app e due domande da discutere insieme.
- **Test**: ogni settimana ha il suo test conclusivo di 30 domande, uguali per entrambi. C'è poi un esame finale di 30 domande su tutto il mese. Ogni risposta ha la sua spiegazione.
- **Allenamento libero**: un test di 10 domande quando volete, che non dà punti, con domande solo sulle settimane che avete già completato, prese dai test o scritte da Claude.
- **La sfida**: si salvano tutti i punteggi. Ogni test settimanale e l'esame finale si fanno una sola volta e valgono un punto per chi ha il risultato migliore; in caso di pareggio un punto a testa. Dopo la consegna il test si può solo rivedere. Una tabella confronta i vostri record e mostra gli ultimi test.
- **Votazione**: l'argomento del mese successivo lo scegliete voi. Si propongono 5 argomenti, scritti a mano o suggeriti da Claude. Ognuno ha 3 voti da dare a 3 argomenti diversi, al massimo uno per argomento. I voti dell'altro restano nascosti finché non avete votato entrambi. Vince l'argomento con più voti. In caso di pareggio potete cambiare i voti o tirare a sorte. Gli slot partono vuoti: gli argomenti si scrivono a mano o si fanno proporre da Claude. Quando la votazione è chiusa, nella stessa pagina compare l'argomento del mese successivo e, una volta preparato, il suo programma.
- **Temi**: ogni argomento appartiene a uno di questi dieci temi: geopolitica, storia, arte, letteratura, economia, politica, scienza, filosofia, tecnologia, cultura. Claude propone solo argomenti con un tema valido, e le 5 proposte di una votazione hanno temi diversi tra loro.
- **Archivio**: tutti i mesi studiati, con i risultati di ciascuno.

## Nomi

Al primo accesso l'app chiede a ciascuno come vuole essere chiamato. Il nome compare nei progressi, nella sfida e nella votazione, e si può cambiare in qualsiasi momento toccando il proprio nome in alto. Ognuno può modificare solo il proprio.

## Dove si usa

L'app è pubblicata come Artifact su claude.ai. Lì i dati si salvano in un database condiviso, così i progressi restano sincronizzati tra voi due e su tutti i dispositivi. Lì funziona anche la generazione dei contenuti con Claude. Per usarla in due, il proprietario invita l'altra persona per email dal menu Condividi, con il livello Editor. Non attivate il link pubblico: con il link pubblico attivo, chi è stato invitato da fuori non può salvare.

Se aprite `studiolo/index.html` direttamente nel browser, l'app funziona in modalità locale: i progressi restano solo in quel browser e Claude non è disponibile.

## Struttura

- `studiolo/index.html`: l'intera app (HTML, CSS e JavaScript, senza dipendenze né build).
- `studiolo/seed/`: i contenuti iniziali caricati nel database: il programma di ottobre 2026 (Il Rinascimento italiano, 4 settimane) e i test conclusivi delle settimane.

## Dati salvati

| Collezione | Documento | Contenuto |
|---|---|---|
| `topics` | `AAAA-MM` | programma del mese: capitoli, libri, extra |
| `progress` | `AAAA-MM--<utente>` | settimane completate, lezioni lette, risultati e storico di test, allenamenti ed esame finale |
| `quizzes` | `AAAA-MM--c1` … `AAAA-MM--final` | domande dei test |
| `lessons` | `AAAA-MM--c1--l1` … `--l3` | le tre lezioni di ogni settimana (`--c1--l1`…) e gli approfondimenti (`--dd1`…`--dd10`), scritti da Claude |
| `votes` | `AAAA-MM` | votazione del mese: 5 candidati, stato, vincitore |
| `names` | `<utente>` | nome scelto da ciascun partecipante; ognuno può modificare solo il proprio |
| `ballots` | `<utente>` | voti di ciascuno; ognuno può modificare solo i propri |
