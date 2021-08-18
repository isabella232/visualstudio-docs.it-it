---
title: Linee guida per Developer Community
description: Vengono descritte le linee guida per l'uso Visual Studio Developer Community.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 7e007c87a855ae5c05cce1b48e36edb166cd9762
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137413"
---
# <a name="developer-community-guidelines"></a>Linee guida per Developer Community

Il portale per Community tiene traccia dei problemi e dei suggerimenti sulle funzionalità per Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Invio di problemi e suggerimenti

Il [Visual Studio developer Community](https://aka.ms/feedback/suggest?space=8) tiene traccia dei problemi e dei suggerimenti sulle funzionalità per Visual Studio.

### <a name="before-submitting-an-issue"></a>Prima di inviare un problema

Cercare il problema in Visual Studio Developer Community per assicurarsi che non esista già. Se il problema esiste già, inserire commenti pertinenti e esprimere il proprio voto.

Se il problema è una domanda, chiedere alla community di [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) usando il tag _visual-studio_. Il personale di supporto clienti monitora tale tag e consente di rispondere alle domande.

Se non è possibile trovare un problema esistente che descrive il bug o la funzionalità, inviare un problema usando le linee guida seguenti.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Scrittura di un report di bug o di un suggerimento di funzionalità corretto

- Mettere solo un problema o una richiesta di funzionalità per problema.

  - La combinazione di più problemi o richieste di funzionalità in un singolo problema rende più difficile la diagnosi e più difficile per altri utenti votare per il problema.
  - Non aggiungere il problema come commento a un problema esistente a meno che non si tratti di un input identico. Molti problemi hanno un aspetto simile, ma hanno cause diverse, il che rende più difficile la diagnosi del problema.

- Più informazioni è possibile fornire, più sarà facile riprodurre e risolvere il problema.
- Includere i passaggi seguenti con ogni problema.

  - Passaggi riproducibili (1... 2... 3...) e ciò che ci si aspetta rispetto a ciò che si è verificato.
  - Immagini, animazioni o un collegamento a un video. Le immagini e le animazioni illustrano i passaggi di _riproduzione, ma non li_ sostituiscono.
  - In base alle esigenze, un frammento di codice che illustra il problema o un collegamento a un repository di codice può essere facilmente inserito nel computer per ricreare il problema.

- Ricordarsi di seguire questa procedura:

  - Cercare per verificare se esiste un duplicato. In tal caso, votare il problema esistente, fornendo commenti o chiarimenti aggiuntivi in base alle esigenze.
  - Ricreare il problema dopo aver disabilitato tutte le estensioni. Se si individua che il problema è causato da un'estensione installata, determinare un problema rispettivamente nell'estensione.
  - Semplificare il codice intorno al problema in modo da poterlo isolare meglio.

Anche con problemi che includono dettagli completi, potrebbe non essere possibile riprodurre il problema e potrebbe richiedere altre informazioni.

## <a name="managing-problem-reports"></a>Gestione delle segnalazioni di problemi

La analisi di un problema è un processo in più passaggi che viene eseguito in modo collaborativo all'interno del team di funzionalità. La ricerca di dati richiede in genere una settimana, ma può richiedere più tempo. L'obiettivo della valuta è fornire una comprensione chiara di ciò che accadrà al problema. Dopo la valuta, ad esempio, si sa se si prevede di risolvere il problema o di attendere altri commenti e suggerimenti della community.

Dopo la segnalazione di un problema, gli stati indicano la fase in cui si trovano le informazioni inviate nel proprio ciclo di vita. Quando Visual Studio team del prodotto esaminano i commenti e suggerimenti, impostano lo stato appropriato. Tenere traccia dello stato di avanzamento delle segnalazioni di problemi facendo riferimento agli [stati del problema e alle domande frequenti.](./report-a-problem.yml)

### <a name="prioritizing-which-issues-to-fix"></a>Definizione delle priorità per i problemi da risolvere

Non è possibile risolvere tutti i problemi segnalati. Alcune sono troppo costose da correggere, altre potrebbero regredire in altre aree di funzionalità e altre potrebbero avere un impatto troppo basso. È possibile che ciò possa risultare molto utile se si è preso tempo per inviare una segnalazione del problema. Siamo stati tutti presenti, in questo progetto o in altri progetti a cui abbiamo contribuito. Se un problema è stato chiuso e il motivo per cui è stato dato non è soddisfatto, è possibile chiarire il caso d'uso e richiedere che il problema sia nuovamente attivato per un altro passaggio. A questo punto, è possibile richiedere altre informazioni.

### <a name="missing-important-information"></a>Informazioni importanti mancanti

Quando a un problema mancano informazioni importanti, viene assegnato lo _stato Necessita di altre_ informazioni. Si commenta il problema con le informazioni specifiche necessarie e si riceverà una notifica tramite posta elettronica. Se le informazioni non vengono ricevute entro sette giorni, viene inviato un promemoria. Successivamente, il ticket viene chiuso dopo 14 giorni di inattività.

### <a name="other-product"></a>Altro prodotto

In alcuni casi, quando si segnala un problema, si verifica che è causato da un altro prodotto e non Visual Studio. Potrebbe trattarsi di un'altra applicazione correlata o di un'estensione. 

In questo caso, il problema verrà chiuso e verrà chiesto di aprirlo con l'altro prodotto. Di seguito sono riportati alcuni punti comuni in cui vengono riportati questi problemi:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio Supporto della sottoscrizione](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Informazioni aggiuntive

- [Come aumentare le probabilità che venga risolto un problema di prestazioni](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Risolvere i problemi e creare i log per problemi relativi a MSBuild](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Gestione dei suggerimenti sulle funzionalità

I suggerimenti di funzionalità sono un mezzo di comunicazione tra microsoft e i membri della community di sviluppatori. Tecnicamente, è possibile mantenere aperte tutte le richieste di funzionalità per sempre. Ma mantenere aperti i problemi ridurrebbe la visibilità della community sullo stato effettivo di una funzionalità. Si chiudono quindi le richieste di funzionalità non indirizzate e si assegnano le funzionalità che potrebbero essere indirizzate _all'etichetta Under Review (Revisione_ in corso).

Se è stata suggerita una funzionalità, è possibile che non si prevede di affrontare la richiesta. Questo è comprensibile. Tutti gli utenti sono stati presenti in questo progetto o in altri progetti a cui abbiamo contribuito. Tutti i dati di input sono molto amori. Non adottare offesa personale quando si chiude o si assegna _l'etichetta Sotto_ revisione al suggerimento. Se si desidera che il suggerimento di funzionalità rimanga aperto, chiarire il caso d'uso e contattare Microsoft o raccogliere più voti.

Nel processo decisionale vengono trattate le caratteristiche seguenti relative al suggerimento di funzionalità:

- Corrisponde alla direzione generale del prodotto?
- Ci si può permettere di crearlo e gestirlo?
- È in linea con la strategia complessiva [della roadmap?](/visualstudio/productinfo/vs-roadmap)
- Ha il supporto della community, come indicato da voti e commenti?
- È un servizio molto ami, anche con un basso supporto della community?

Quando non è possibile rispondere "sì" a una di queste domande, la si chiuderà. Ma spesso il suggerimento rimane aperto come In fase _di revisione per_ raccogliere altri commenti e suggerimenti della community.

Se un suggerimento non corrisponde alla direzione complessiva del prodotto, verrà chiuso come *Fuori ambito.* Ad esempio, potrebbero esserci investimenti simili in altri membri della Visual Studio famiglia di prodotti. In caso contrario, la funzionalità suggerita potrebbe essere rilevante solo per alcune persone, rendendo un'estensione più adatta a fornirla.

Tenere traccia dello stato di avanzamento del suggerimento di funzionalità facendo riferimento agli stati [di suggerimento e alle domande frequenti.](./report-a-problem.yml)

## <a name="discussion-etiquette"></a>Etichetta di discussione

Per mantenere la conversazione chiara e trasparente, limitare la discussione all'inglese e mantenere gli elementi rilevanti per il problema. Essere premuosi gli altri e cercare sempre di essere cortesi e professionali.

Per altre informazioni, vedere il [Codice di comportamento Community Microsoft.](https://answers.microsoft.com/en-us/page/codeofconduct)

Eventuali violazioni all'etichetta di discussione possono portare alla rimozione del commento e infine al divieto dell'utente.

## <a name="data-privacy"></a>Privacy dei dati

I commenti e le risposte sono visibili pubblicamente, ma tutti i file allegati vengono condivisi privatamente solo con Microsoft. Questa visibilità è utile perché consente all'intera community di visualizzare i problemi e le soluzioni rilevati da altri utenti. Se si è interessati alla privacy dei dati o dell'identità, sono disponibili opzioni. Altre informazioni sulla privacy [dei dati Community developer.](./developer-community-privacy.md)

## <a name="next-steps"></a>Passaggi successivi

Passare alla pagina Visual Studio [Developer Community](https://aka.ms/feedback/suggest?space=8) segnalare problemi, suggerire funzionalità o esplorare i ticket esistenti. Buon lavoro.
