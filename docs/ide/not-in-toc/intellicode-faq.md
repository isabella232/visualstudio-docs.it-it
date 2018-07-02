---
title: Domande e risposte su IntelliCode
ms.date: 05/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: f0410b3ffd04c42f316d99c150253e72bb1b1944
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34468804"
---
# Domande frequenti su Visual Studio IntelliCode

Grazie per l'interesse dimostrato per Visual Studio IntelliCode. Questo breve documento di domande frequenti ha lo scopo di rispondere, auspicabilmente, ad alcune delle domande degli utenti.

## D. Che cos'è Visual Studio IntelliCode?

In Build 2018 è stato annunciato il rilascio di Visual Studio IntelliCode, una nuova funzionalità in grado di migliorare lo sviluppo di software tramite l'intelligenza artificiale. IntelliCode consente agli sviluppatori e ai team di scrivere codice con sicurezza, individuare i problemi più rapidamente ed eseguire revisioni del codice mirate.

È già stato illustrato in che modo IntelliCode garantisca il miglioramento del processo di sviluppo di software tramite:

- Completamento del codice con riconoscimento del contesto
- Guida per gli sviluppatori per il rispetto dei criteri e degli stili usati dal team
- Individuazione di problemi del codice difficili da trovare
- Revisioni del codice mirate, che pongono al centro dell'attenzione le aree realmente importanti

Gli sviluppatori possono cercare altre informazioni e registrarsi per ricevere le novità e le anteprime private future all'indirizzo [ https://aka.ms/intellicode ](https://aka.ms/intellicode).

## D. Cosa sono in grado di fare i clienti con Visual Studio IntelliCode?

Visual Studio IntelliCode è una gamma di funzionalità in grado di realizzare un miglioramento innovativo della produttività tramite l'impiego dell'intelligenza artificiale (AI).

Gli sviluppatori possono [scaricare un'estensione sperimentale](https://go.microsoft.com/fwlink/?linkid=872707) per Visual Studio 2017 versione 15.7 e successive. L'estensione offre una versione di IntelliSense avanzata in grado di suggerire l'API probabilmente corretta per l'uso da parte dello sviluppatore, anziché limitarsi a visualizzare un elenco alfabetico di membri. Per visualizzare l'elenco dinamico, usa il contesto e i criteri correnti del codice dello sviluppatore. Nei prossimi mesi l'estensione verrà aggiornata con altre funzionalità.

## D. Vi sono altre funzionalità disponibili per l'estensione di Visual Studio IntelliCode? Ad esempio, la generazione di editorConfig?

Numerose funzionalità sono attualmente oggetto di sviluppo; verranno condivise pubblicamente appena diventeranno disponibili. In occasione di Microsoft Build 2018 è stata anticipata una versione per uso interno di uno strumento che consente di inferire le impostazioni di editorConfig per lo stile e la formattazione di codice in C#. Non si tratta ancora dell'estensione sperimentale ma contiamo di renderla disponibile a breve. È possibile registrarsi per avere notizie e aggiornamenti all'indirizzo [https://aka.ms/intellicode](https://aka.ms/intellicode) per conoscere in anteprima le nuove funzionalità disponibili.

## D: Che cosa rende "IntelliSense assistito dall'intelligenza artificiale" con tecnologia IntelliCode migliore della versione normale di IntelliSense?

Con IntelliCode, l'elenco di completamento suggerisce l'API che con ogni probabilità è la più corretta per l'uso da parte dello sviluppatore, anziché limitarsi a visualizzare un semplice elenco alfabetico di membri. Per visualizzare l'elenco dinamico, IntelliSense usa il contesto del codice corrente dello sviluppatore e criteri basati su 2000 progetti open source di qualità elevata in GitHub, ognuno con oltre 100 stelle. I risultati formano un modello in grado di prevedere le chiamate API più probabili e pertinenti.

## D: Qual è la qualità dei suggerimenti di completamento IntelliCode?

I suggerimenti di IntelliCode sono stati usati internamente a Microsoft per un certo tempo e riteniamo che siano utili. In definitiva, tuttavia, la conferma dell'utilità di questi suggerimenti dovrà arrivare dagli sviluppatori che li usano durante la scrittura del codice. Invitiamo i nostri clienti a provare l'[estensione IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) di Visual Studio e a inviare commenti e suggerimenti sul funzionamento. Il modello verrà anche sottoposto a training in base ai suggerimenti scelti dai clienti e l'estensione verrà aggiornata man mano che il modello migliora.

> [!NOTE]
> Non verrà raccolto alcun codice definito dall'utente. Vedere la domanda relativa alla [privacy](#privacy).

## D. Qual è il futuro di IntelliCode?

È in corso l'analisi di un'ampia gamma di soluzioni per migliorare la produttività degli sviluppatori tramite l'intelligenza artificiale e altre tecniche avanzate. In occasione di Microsoft Build 2018 è stata offerta un'anteprima di alcuni degli scenari in cui l'intelligenza artificiale può essere d'aiuto agli sviluppatori, ma ne esistono molti altri. Il contributo degli sviluppatori che sperimentano quanto illustrato è di grande interesse. Questi sono quindi invitati a registrarsi all'indirizzo [ https://aka.ms/intellicode ](https://aka.ms/intellicode) per ricevere novità e aggiornamenti.

## D. Quanto costa?

Al momento non ci sono annunci relativi ai prezzi.

## D. Quando verrà rilasciato IntelliCode?

IntelliSense assistito dall'intelligenza artificiale di IntelliCode è attualmente nella prima fase di anteprima sperimentale. L'estensione sperimentale continuerà in futuro a essere aggiornata con nuove funzionalità. Non è disponibile alcuna pianificazione per la versione finale, ma commenti e suggerimenti da parte degli sviluppatori sono bene accetti, perché consentono di offrire la migliore esperienza possibile. È possibile ricevere novità e aggiornamenti registrandosi all'indirizzo [ https://aka.ms/intellicode ](https://aka.ms/intellicode).

## D. Questa esperienza è disponibile solo in Visual Studio e per C#?

In Build 2018 l'esperienza è stata illustrata con una codebase C# in Visual Studio 2017. IntelliCode verrà tuttavia espanso il più presto possibile a un numero maggiore di linguaggi e strumenti della famiglia Visual Studio in futuro.

## D. <a name="whynointellisense"/> Perché non riesco a visualizzare i suggerimenti IntelliCode in C#?

I suggerimenti IntelliCode vengono visualizzati nell'esperienza di Visual Studio IntelliSense standard per C#. Le estensioni che eseguono l'override di tale esperienza impediscono la visualizzazione dei suggerimenti IntelliCode nella parte superiore dell'elenco. È possibile verificare se sono le estensioni a provocare questo comportamento disattivandole e riprovando a usare IntelliSense.

Se in questo modo il problema non si risolve, eseguire una segnalazione tramite la funzionalità di Visual Studio [Segnala un problema](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) e indicare IntelliCode nella segnalazione.

## D. Quale versione di Visual Studio è necessaria per eseguire questa estensione?

L'estensione IntelliCode per Visual Studio è supportata in Visual Studio 2017 versione 15.7 Preview 5 e versioni successive (tutti gli SKU). L'installazione dell'estensione si interrompe con l'errore "Questa estensione non è installabile su nessuno dei prodotti attualmente installati." se non è installata la versione minima richiesta.

## D. Questa esperienza è disponibile solo in inglese?

IntelliCode è un'estensione di anteprima al momento e desideriamo prima di tutto capire quanto siano utili queste funzionalità per un ampio gruppo di clienti. Quando decideremo di uscire dalla versione di anteprima per IntelliCode, verranno senz'altro valutate le impostazioni locali o le lingue da supportare per prime, oltre alle caratteristiche del pacchetto, in base ai commenti e ai suggerimenti dei clienti.

## <a name="privacy"/> D: E dal punto di vista della privacy? Il codice viene inviato nel cloud? Quali dati dei clienti vengono inviati a Microsoft?

Gli sviluppatori sono invitati a provare Visual Studio IntelliCode fin da oggi come estensione di anteprima sperimentale. Lo scopo dell'estensione è di consentire agli sviluppatori di provare le funzionalità di IntelliCode e inviare commenti e suggerimenti al team del prodotto.

Per favorire il miglioramento del prodotto, vengono acquisiti in forma anonima alcuni dati sull'utilizzo e sugli errori. A Microsoft non viene inviato codice scritto dagli utenti, ma vengono raccolte informazioni sull'uso dei risultati di IntelliCode. I dati includono solo tipi e membri open source e .NET selezionati dagli utenti dall'elenco di suggerimenti di IntelliCode. Gli sviluppatori possono rifiutare esplicitamente il programma [Analisi utilizzo software di Visual Studio](../../ide/visual-studio-experience-improvement-program.md). In questo caso viene disattivata anche la raccolta dei dati per l'estensione IntelliCode. Dalla barra dei menu selezionare **?** > **Invia feedback** > **Impostazioni**. Nella finestra di dialogo **Analisi utilizzo software di Visual Studio** selezionare **No, non voglio partecipare** e quindi selezionare **OK**.

L'estensione IntelliCode può periodicamente chiedere allo sviluppatore di completare un sondaggio, anche questo anonimo. Gli utenti possono registrarsi per ricevere novità e un'anteprima privata futura, ma attualmente per usare l'estensione sperimentale non è necessario eseguire questa operazione.

Le funzionalità future potranno richiedere l'accesso a un servizio per il quale sia necessaria la registrazione. Altri dettagli verranno pubblicati quando tali funzionalità saranno pronte per l'anteprima privata.
