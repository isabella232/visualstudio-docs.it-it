---
title: Linee guida per Developer Community
description: Descrive le linee guida per l'uso della community degli sviluppatori di Visual Studio.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e30dcb6a9d65cb562851ed90e350530759975d2
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668560"
---
# <a name="developer-community-guidelines"></a>Linee guida per Developer Community

La community degli sviluppatori tiene traccia dei problemi e dei suggerimenti sulle funzionalità di Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Invio di problemi e suggerimenti

La [community degli sviluppatori di Visual Studio](https://aka.ms/feedback/suggest?space=8) tiene traccia dei problemi e suggerimenti sulle funzionalità di Visual Studio.

### <a name="before-submitting-an-issue"></a>Prima di inviare un problema

Cercare il problema nella community degli sviluppatori di Visual Studio per assicurarsi che non esista già. Se il problema persiste, effettuare i commenti pertinenti ed eseguire il cast dei voti.

Se il problema è una domanda, rivolgersi alla community [stack overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) usando il tag _Visual-Studio_. Il personale del supporto tecnico del cliente è in grado di monitorare questo tag e fornirà assistenza per rispondere alle domande.

Se non si riesce a trovare un problema esistente che descrive il bug o la funzionalità, inviare un problema usando le linee guida riportate di seguito.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Creazione di un report di bug o di un suggerimento di funzionalità valido

- Consente di archiviare solo un problema o una richiesta di funzionalità per ogni problema.

  - La combinazione di più problemi o richieste di funzionalità in un singolo problema rende più difficile la diagnosi e la maggior parte degli altri utenti a votare il problema.
  - Non aggiungere il problema come commento a un problema esistente a meno che non si tratti di un input identico. Molti problemi hanno un aspetto simile, ma hanno diverse cause, il che rende più difficile la diagnosi del problema.

- Maggiori sono le informazioni che è possibile fornire, più semplice sarà la riproduzione e la risoluzione del problema.
- Per ogni problema, includere i passaggi seguenti.

  - Passaggi riproducibili (1... 2... 3...) e ciò che ci aspettavamo rispetto a quello che hai sperimentato.
  - Immagini, animazioni o un collegamento a un video. Le immagini e le animazioni illustrano la procedura di ripetizione, ma _non_ la sostituiscono.
  - A seconda dei casi, un frammento di codice che illustra il problema o un collegamento a un repository di codice può facilmente accedere al computer per ricreare il problema.

- Ricordarsi di eseguire i passaggi seguenti:

  - Eseguire una ricerca per verificare se esiste un duplicato. In tal caso, votare il problema esistente, fornendo commenti o chiarimenti aggiuntivi in base alle esigenze.
  - Ricreare il problema dopo aver disabilitato tutte le estensioni. Se il problema è causato da un'estensione installata, archiviare rispettivamente un problema nell'estensione.
  - Semplificare il codice intorno al problema in modo da poterlo isolare meglio.

Anche in caso di problemi che includono dettagli avanzati, potrebbe non essere possibile riprodurre il problema e richiedere ulteriori informazioni.

## <a name="managing-problem-reports"></a>Gestione dei report di problemi

La valutazione di un problema è un processo in più passaggi che viene eseguito in modo collaborativo all'interno del team di funzionalità. Il Triaging richiede in genere una settimana, ma potrebbe richiedere più tempo. L'obiettivo del Triaging è fornire una chiara comprensione delle conseguenze del problema. Ad esempio, dopo la valutazione è possibile stabilire se si prevede di risolvere il problema o attendere un ulteriore feedback della community.

Dopo la segnalazione di un problema, gli stati indicano la fase in cui si trovano le informazioni inviate nel proprio ciclo di vita. Poiché i team dei prodotti Visual Studio esaminano il feedback, lo impostano con uno stato appropriato. Tenere traccia dello stato di avanzamento dei report dei problemi facendo riferimento agli [Stati del problema e alle domande frequenti](./report-a-problem.md).

### <a name="prioritizing-which-issues-to-fix"></a>Assegnazione di priorità ai problemi da correggere

Non è possibile risolvere tutti i problemi segnalati. Alcuni sono troppo costosi da correggere, altri potrebbero regredire altre aree di funzionalità e altri potrebbero avere un effetto troppo basso. Questo potrebbe risultare deludente se è stato richiesto di inviare un report sui problemi. Siamo stati tutti disponibili, sia in questo progetto che in altri utenti a cui è stato contribuito. Se un problema è stato chiuso e si ritiene che il motivo per cui è stato fornito non sia soddisfacente, è possibile chiarire il caso d'uso e richiedere che il problema venga riattivato per un altro passaggio. A questo punto, è possibile richiedere ulteriori informazioni.

### <a name="missing-important-information"></a>Informazioni importanti mancanti

Quando in un problema mancano informazioni importanti, viene assegnato lo stato _needs more info (altre informazioni_ ). Il problema viene commentato con le informazioni specifiche necessarie e si riceverà una notifica tramite posta elettronica. Se le informazioni non vengono ricevute entro sette giorni, viene inviato un promemoria. Successivamente, il ticket viene chiuso dopo 14 giorni di inattività.

### <a name="other-product"></a>Altro prodotto

In alcuni casi, quando si segnala un problema, la causa è causata da un altro prodotto e non da Visual Studio. Potrebbe trattarsi di un'altra applicazione correlata o di un'estensione. 

In tal caso, il problema verrà chiuso e verrà chiesto di aprirlo con l'altro prodotto. Di seguito sono riportate alcune posizioni comuni per archiviare i problemi:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Supporto per le sottoscrizioni di Visual Studio](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Informazioni aggiuntive

- [Come aumentare le probabilità di correzione di un problema di prestazioni](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Risolvere i problemi e creare i log per problemi relativi a MSBuild](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Gestione dei suggerimenti sulle funzionalità

I suggerimenti sulle funzionalità rappresentano un mezzo di comunicazione tra Microsoft e i membri della community degli sviluppatori. Tecnicamente, è possibile che tutte le richieste di funzionalità rimangano aperte per sempre. Tuttavia, mantenere aperti i problemi ridurrebbe la visibilità della community sullo stato effettivo di una funzionalità. Si chiudono quindi le richieste di funzionalità che non verranno indirizzate e verranno assegnate le funzionalità che potrebbero essere indirizzate all'etichetta _sotto la revisione_ .

Se è stata suggerita una funzionalità, è possibile che non si preveda di risolvere la richiesta. È chiaro che. Ci siamo già presenti in questo progetto o in altri utenti a cui è stato contribuito. Quindi, assicuratevi che tutti gli input siano apprezzati. Non intraprendere un attacco personale quando si chiude o si assegna l'etichetta _in revisione_ al suggerimento. Se si ritiene che il suggerimento per le funzionalità meriti di rimanere aperto, chiarire il caso d'uso e contattarci o raccogliere più voti.

Nel processo decisionale si osserveranno le seguenti caratteristiche relative al suggerimento sulle funzionalità:

- Corrisponde alla direzione generale del prodotto?
- È possibile consentirne la compilazione e la gestione?
- Si allineano alla strategia di [Roadmap](/visualstudio/productinfo/vs-roadmap) complessiva?
- Dispone del supporto della community, come indicato da voti e commenti?
- Ci piace anche con il supporto della community di basso livello?

Se non è possibile rispondere a queste domande, verrà chiusa. Tuttavia, spesso il suggerimento resterà aperto come _Revisione_ per raccogliere altri commenti della community.

Se un suggerimento non corrisponde alla direzione generale del prodotto, verrà chiuso come *fuori ambito*. Potrebbero ad esempio essere presenti investimenti simili in altri membri della famiglia di prodotti Visual Studio. In alternativa, la funzionalità suggerita potrebbe essere rilevante solo per alcune persone, rendendo un'estensione più adatta per fornirla.

Tenere traccia dello stato di avanzamento del suggerimento per le funzionalità facendo riferimento agli [stati dei suggerimenti e alle domande frequenti](./report-a-problem.md).

## <a name="discussion-etiquette"></a>Galateo discussione

Per rendere chiara e trasparente la conversazione, limitare la discussione all'inglese e tener presente le informazioni rilevanti per il problema. Sii attento ad altri e prova sempre a essere cortese e professionale.

Per ulteriori informazioni, vedere la pagina relativa al [codice di comportamento della community Microsoft](https://answers.microsoft.com/en-us/page/codeofconduct).

Eventuali violazioni al galateo di discussione possono causare la rimozione del commento e la fine del divieto dell'utente.

## <a name="data-privacy"></a>Privacy dei dati

I commenti e le risposte sono visibili pubblicamente, ma tutti i file allegati sono condivisi privatamente solo con Microsoft. Questa visibilità è vantaggiosa perché consente all'intera community di visualizzare i problemi e le soluzioni rilevati da altri utenti. Se si è interessati alla privacy dei dati o dell'identità, sono disponibili opzioni. Scopri di più sulla [privacy dei dati della community degli sviluppatori](./developer-community-privacy.md).

## <a name="next-steps"></a>Passaggi successivi

Passa alla [community degli sviluppatori di Visual Studio](https://aka.ms/feedback/suggest?space=8) per segnalare problemi, suggerire funzionalità o esplorare i ticket esistenti. Buon lavoro.
