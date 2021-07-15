---
title: Linee guida per Developer Community
description: Vengono descritte le linee guida per l'uso Visual Studio Developer Community.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21cf3bd6a0c208a78cd391f93702865e905482e0
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756891"
---
# <a name="developer-community-guidelines"></a>Linee guida per Developer Community

L'Community per sviluppatori tiene traccia dei problemi e dei suggerimenti di funzionalità per Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Invio di problemi e suggerimenti

Il [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8) tiene traccia dei problemi e dei suggerimenti di funzionalità per Visual Studio.

### <a name="before-submitting-an-issue"></a>Prima di inviare un problema

Cercare il problema in Visual Studio Developer Community per assicurarsi che non esista già. Se il problema esiste già, inserire commenti pertinenti e votare.

Se il problema è una domanda, chiedere alla community di [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) usando il tag _visual-studio_. Il personale del supporto clienti monitora il tag e consente di rispondere alle domande.

Se non è possibile trovare un problema esistente che descrive il bug o la funzionalità, inviare un problema usando le linee guida seguenti.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Scrittura di un report di bug o di un suggerimento di funzionalità

- File solo un problema o una richiesta di funzionalità per problema.

  - La combinazione di più problemi o richieste di funzionalità in un singolo problema rende più difficile la diagnosi e il voto degli altri utenti per il problema.
  - Non aggiungere il problema come commento a un problema esistente a meno che non si tratti di un input identico. Molti problemi hanno un aspetto simile, ma hanno cause diverse, il che rende più difficile la diagnosi del problema.

- Più informazioni è possibile fornire, più sarà facile riprodurre e risolvere il problema.
- Includere i passaggi seguenti con ogni problema.

  - Passaggi riproducibili (1... 2... 3...) e ciò che ci si aspetta rispetto a ciò che si è verificato.
  - Immagini, animazioni o un collegamento a un video. Le immagini e le animazioni illustrano i passaggi di _riproduzione, ma non li_ sostituiscono.
  - In base alle esigenze, un frammento di codice che illustra il problema o un collegamento a un repository di codice è possibile eseguire facilmente il pull verso il basso nel computer per ricreare il problema.

- Ricordarsi di seguire questa procedura:

  - Cercare per verificare se esiste un duplicato. In tal caso, votare il problema esistente, fornendo commenti o chiarimenti aggiuntivi in base alle esigenze.
  - Ricreare il problema dopo la disabilitazione di tutte le estensioni. Se il problema è causato da un'estensione installata, determinare un problema rispettivamente nell'estensione.
  - Semplificare il codice intorno al problema in modo da poterlo isolare meglio.

Anche con problemi che includono dettagli completi, potrebbe non essere possibile riprodurre il problema e potrebbe richiedere altre informazioni.

## <a name="managing-problem-reports"></a>Gestione dei report sui problemi

La analisi di un problema è un processo in più passaggi che viene eseguito in modo collaborativo all'interno del team di funzionalità. La ricerca richiede in genere una settimana, ma può richiedere più tempo. L'obiettivo della ricerca è fornire una chiara comprensione di ciò che accadrà al problema. Ad esempio, dopo la triage si sa se si prevede di risolvere il problema o di attendere altri commenti e suggerimenti della community.

Dopo la segnalazione di un problema, gli stati indicano la fase in cui si trovano le informazioni inviate nel proprio ciclo di vita. Quando Visual Studio team del prodotto esaminano i commenti e suggerimenti, lo impostano con uno stato appropriato. Tenere traccia dello stato delle segnalazioni di problemi facendo riferimento agli [stati del problema e alle domande frequenti.](./report-a-problem.yml)

### <a name="prioritizing-which-issues-to-fix"></a>Assegnazione della priorità ai problemi da risolvere

Non è possibile risolvere tutto il problema segnalato. Alcune sono troppo costose da correggere, altre potrebbero regredire in altre aree di funzionalità e altre potrebbero avere un impatto troppo basso. Si è compreso che ciò potrebbe risultare insodd disderci se si è preso il tempo necessario per inviare una segnalazione del problema. Ci siamo stati tutti, in questo progetto o in altri progetti a cui abbiamo contribuito. Se un problema è stato chiuso e si ritieni che il motivo fornito non sia soddisfacente, puoi chiarire il caso d'uso e richiedere che il problema sia ri-attivato per un altro passaggio. A questo punto, è possibile richiedere altre informazioni.

### <a name="missing-important-information"></a>Informazioni importanti mancanti

Quando un problema non contiene informazioni importanti, viene assegnato lo _stato Altre_ informazioni necessarie. Si commenta il problema con le informazioni specifiche necessarie e si riceverà una notifica tramite posta elettronica. Se le informazioni non vengono ricevute entro sette giorni, verrà inviato un promemoria. Successivamente, il ticket viene chiuso dopo 14 giorni di inattività.

### <a name="other-product"></a>Altro prodotto

A volte quando si segnala un problema, risulta essere causato da un altro prodotto e non da Visual Studio. Potrebbe trattarsi di un'altra applicazione correlata o di un'estensione. 

In questo caso, il problema verrà chiuso e verrà chiesto di aprirlo con l'altro prodotto. Di seguito sono riportati alcuni punti comuni in cui è possibile descrizione di questi problemi:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio Supporto della sottoscrizione](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Informazioni aggiuntive

- [Come aumentare le probabilità di correzione di un problema di prestazioni](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Risolvere i problemi e creare i log per problemi relativi a MSBuild](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Gestione dei suggerimenti per le funzionalità

I suggerimenti per le funzionalità sono un mezzo di comunicazione tra microsoft e i membri della community di sviluppatori. Tecnicamente, è possibile mantenere tutte le richieste di funzionalità aperte per sempre. Ma mantenere aperti i problemi ridurrebbe la visibilità della community sullo stato effettivo di una funzionalità. Pertanto, le richieste di funzionalità non vengono indirizzate e vengono assegnate le funzionalità che potrebbero essere indirizzate _all'etichetta Sotto_ revisione.

Se è stata suggerita una funzionalità, si potrebbe essere rimasti delusi dal fatto che non si prevede di risolvere la richiesta. Questo è comprensibile. Tutti gli utenti sono stati presenti in questo progetto o in altri progetti a cui abbiamo contribuito. Quindi, siamo certi che tutti i tuoi input sono molto amate. Non prendere offesa personale quando chiudiamo o assegniamo _l'etichetta Sotto_ revisione al suggerimento. Se il suggerimento della funzionalità merita di rimanere aperto, chiarire il caso d'uso e contattare Microsoft o raccogliere più voti.

Nel processo decisionale vengono trattate le caratteristiche seguenti relative al suggerimento di funzionalità:

- Corrisponde alla direzione generale del prodotto?
- È possibile permettersi di crearlo e gestirlo?
- È in linea con la strategia di [roadmap](/visualstudio/productinfo/vs-roadmap) complessiva?
- Ha il supporto della community, come indicato da voti e commenti?
- Ci piace, anche con un basso supporto della community?

Quando non è possibile rispondere "sì" a una di queste domande, la si chiude. Ma spesso il suggerimento rimane aperto come _Sotto revisione_ per raccogliere altri commenti e suggerimenti della community.

Se un suggerimento non corrisponde alla direzione complessiva del prodotto, verrà chiuso come *Fuori ambito.* Ad esempio, si potrebbero avere investimenti simili in altri membri della Visual Studio di prodotti. In caso contrario, la funzionalità suggerita potrebbe essere pertinente solo per poche persone, rendendo un'estensione più adatta per fornirla.

Tenere traccia dello stato di avanzamento del suggerimento di funzionalità facendo riferimento agli stati [dei suggerimenti e alle domande frequenti.](./report-a-problem.yml)

## <a name="discussion-etiquette"></a>Etichetta di discussione

Per mantenere la conversazione chiara e trasparente, limitare la discussione all'inglese e mantenere le informazioni rilevanti per il problema. Essere premurosi per gli altri e cercare sempre di essere cortesi e professionali.

Per altre informazioni, vedere [il Codice di Community microsoft.](https://answers.microsoft.com/en-us/page/codeofconduct)

Qualsiasi violazione dell'etichetta di discussione può comportare la rimozione del commento e infine il divieto dell'utente.

## <a name="data-privacy"></a>Privacy dei dati

I commenti e le risposte sono visibili pubblicamente, ma tutti i file allegati vengono condivisi privatamente solo con Microsoft. Questa visibilità è vantaggiosa perché consente all'intera community di visualizzare i problemi e le soluzioni trovati da altri utenti. Se si è interessati alla privacy dei dati o dell'identità, sono disponibili opzioni. Altre informazioni sulla privacy [dei Community per gli sviluppatori.](./developer-community-privacy.md)

## <a name="next-steps"></a>Passaggi successivi

Passare all'Visual Studio [Developer Community](https://aka.ms/feedback/suggest?space=8) per segnalare problemi, suggerire funzionalità o esplorare i ticket esistenti. Buon lavoro.
