---
title: Come è possibile aumentare le probabilità che un problema di prestazioni venga risolto
description: Ulteriori informazioni e procedure consigliate per l'invio di problemi di prestazioni in Visual StudioAdditional information and best practices for submitting performance issues in Visual Studio
author: madskristensen
ms.author: madsk
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: f5c83a145eb56dcb95c6e9a299c690ae960442c9
ms.sourcegitcommit: 4bcd6abb89feff1cf8251e3ded73fdc30b67e347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2020
ms.locfileid: "81615038"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Come aumentare le probabilità che un problema di prestazioni venga risolto

Lo strumento "[Segnala un problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)" è ampiamente utilizzato dagli utenti di Visual Studio per segnalare una serie di problemi. Il team di Visual Studio individua le tendenze di arresto anomalo e lentezza nei commenti degli utenti e risolve i problemi che interessano un'ampia gamma di utenti. Più un ticket di feedback specifico è, più è probabile che venga diagnosticato e risolto rapidamente dal team del prodotto. Questo documento descrive le procedure consigliate durante la segnalazione di problemi di arresto anomalo o lentezza per renderli più utilizzabili.

## <a name="general-best-practices"></a>Procedure consigliate generali

Visual Studio è una piattaforma complessa e di grandi dimensioni che supporta una moltitudine di linguaggi, tipi di progetto, piattaforme e altro ancora. Le prestazioni sono una funzione di quali componenti vengono installati e attivi in una sessione, le estensioni installate, le impostazioni di Visual Studio, la configurazione del computer e infine la forma del codice in fase di modifica. Dato il numero di variabili, è difficile stabilire se la segnalazione del problema da un utente ha lo stesso problema di fondo di una segnalazione di problema da un altro utente, anche se il sintomo visibile è lo stesso. Dato che, qui ci sono alcune best practice per garantire il vostro rapporto problema specifico ha maggiore probabilità di essere diagnosticato.

**Fornire un titolo il più specifico possibile**

Cercare firme distinte per il problema segnalato e includere il più possibile nel titolo. Se il titolo è descrittivo, è meno probabile che gli utenti con problemi non correlati (ma lo stesso sintomo superficiale) votino o commentino il tuo biglietto, rendendo così più difficile la diagnosi del *tuo* problema.

**In caso di dubbio, registrare un nuovo rapporto di problema**

Molti problemi potrebbero non avere alcuna firma distintiva o passaggi da riprodurre. In questi casi, una nuova relazione è meglio di un upvote o di un commento su un'altra relazione, che segnala un *sintomo*esteriore simile. A seconda del tipo di report, includere file di diagnostica aggiuntivi nel report come descritto più avanti in questo documento.

**Procedure consigliate specifiche del problema**

Di seguito sono descritti i problemi difficili da diagnosticare senza file di diagnostica. Dopo aver identificato il caso che meglio descrive il problema, segui i passaggi di feedback specifici per quel caso.

-   [Arresti anomali:](#crashes) Si verifica un arresto anomalo quando il processo (Visual Studio) termina in modo imprevisto.

-   [Mancata risposta:](#unresponsiveness) VS non risponde per un periodo di tempo prolungato.

-   [Problemi di lentezza:](#slowness-and-high-cpu-issues) Qualsiasi azione specifica in VS è più lenta di quanto desiderato

-   [CPU elevata:](#slowness-and-high-cpu-issues) Periodi prolungati di utilizzo inaspettatamente elevato della CPU

-   [Problemi out-of-process:](#out-of-process-issues) Un problema causato da un processo satellite di Visual Studio

## <a name="crashes"></a>Crashes
Si verifica un arresto anomalo quando il processo (Visual Studio) termina in modo imprevisto.

**Arresti anomali riproducibili direttamente**

Gli arresti anomali riproducibili direttamente sono casi che presentano tutte le caratteristiche seguenti:Directly reproducible crashes are cases that have all the following characteristics:

- Può essere osservato seguendo una serie nota di passaggi

- Può essere osservato su più computer (se disponibile)

- Può essere riprodotto in codice di esempio o in un progetto che può essere collegato o fornito come parte del feedback (se i passaggi comportano l'apertura di un progetto o di un documento)

Per questi problemi, attenersi alla procedura descritta in "[Come segnalare un problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)" ed essere sicuri di includere:

-   I passaggi per riprodurre il problema

-   Un progetto repro autonomo come descritto in precedenza. Se la riproduzione autonoma non è possibile, includi:

    -   Il linguaggio dei progetti\#aperti (C , C , ecc.)

    -   Tipo di progetto (Applicazione console, ASP.NET e così via)


> [!NOTE]
> **Feedback più prezioso:** In questo caso, il feedback più prezioso è il set di passaggi per riprodurre il problema insieme al codice sorgente di esempio.

**Arresti anomali sconosciuti**

Se non sei sicuro di cosa sta causando gli arresti anomali o sembrano casuali, puoi acquisire i dump in locale ogni volta che Visual Studio si arresta in modo anomalo e collegarli a elementi di feedback separati. Per salvare i dump in locale quando Visual Studio si arresta in modo anomalo, eseguire i comandi seguenti in una finestra di comando di amministratore:

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

Personalizzare il conteggio del dump e la cartella dump in base alle esigenze. Ulteriori informazioni su queste impostazioni [sono disponibili qui](/windows/win32/wer/collecting-user-mode-dumps).

> [!NOTE]
> Dump acquisiti utilizzando Task Manager sono suscettibili di essere del numero sbagliato, che li rende meno utilizzabili. La procedura descritta in precedenza è il modo preferito per acquisire un dump dell'heap. Se si desidera utilizzare Task Manager, chiudere quello attualmente in esecuzione, avviare Task Manager\\a 32 bit (%windir% syswow64\\taskmgr.exe) e raccogliere un dump dell'heap da lì.

> [!NOTE] 
> Ogni file dump prodotto da questo metodo avrà una dimensione massima di 4 GB. Assicurarsi di impostare DumpFolder in un percorso con spazio su disco sufficiente o regolare il DumpCount in modo appropriato.

Ogni volta che Visual Studio si arresta in modo anomalo, verrà creato un file di dump **devenv.exe.[ numero].dmp** nella posizione configurata.

Quindi, utilizzare "Segnala un problema..." di Visual Studio Funzionalità. Esso vi permetterà di collegare il dump appropriato.

1.  Individuare il file dump per l'arresto anomalo segnalato (cercare un file con l'ora di creazione corretta)

2.  Se possibile, comprimere\*il file ( .zip) per ridurne le dimensioni prima di inviare un feedback

3.  Seguire i passaggi descritti in "[How to Report a Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)" e collegare il dump dell'heap a un nuovo elemento di feedback.

> [!NOTE] 
> **Feedback più prezioso:** In questo caso, il feedback più prezioso è il dump dell'heap acquisito al momento dell'arresto anomalo.

## <a name="unresponsiveness"></a>Apatia
VS non risponde per un periodo di tempo prolungato.

**Non reattività riproducibile direttamente**

Come descritto nella sezione corrispondente sugli arresti anomali, per i problemi che possono essere facilmente riprodotti, visualizzati su più computer e che possono essere dimostrati in un piccolo esempio, i rapporti di feedback più preziosi sono quelli che includono i passaggi per riprodurre il problema e includono codice sorgente di esempio che dimostra il problema.

**Mancata risposta sconosciuta**

Se una mancata risposta si manifesta in modo imprevedibile, all'occorrenza successiva avviare una nuova istanza di Visual Studio e segnalare un problema da tale istanza.
Nella [schermata "Record",](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)assicurarsi di selezionare la sessione di Visual Studio che non risponde.

Se l'istanza di Visual Studio che non risponde è stata avviata in modalità amministratore, anche la seconda istanza deve essere avviata in modalità amministratore.

>[!NOTE] 
> **Feedback più prezioso:** In questo caso, il feedback più prezioso è il dump dell'heap acquisito al momento della mancata risposta.

## <a name="slowness-and-high-cpu-issues"></a>Lentezza e problemi di CPU elevata

Ciò che rende un problema di utilizzo della CPU di lentezza o elevato, la maggior parte è una traccia delle prestazioni acquisita mentre è in corso l'operazione lenta o l'evento della CPU elevato.

>[!NOTE] 
> Quando possibile, isolare ogni scenario in un report di feedback specifico separato.
Ad esempio, se la digitazione e la navigazione sono entrambe lente, seguire una volta i passaggi riportati di seguito per ogni problema. Ciò consente al team del prodotto di isolare la causa di problemi specifici.

Per ottenere risultati ottimali nell'acquisizione delle prestazioni, attenersi alla seguente procedura:

1.  Se non è già in esecuzione, avere una copia di Visual Studio aperta dove si riprodurrà il problema

    -   Avere tutto impostato per riprodurre il problema. Ad esempio, se è necessario che un determinato progetto venga caricato con un file specifico aperto, assicurarsi che entrambi i passaggi siano stati completati prima di procedere.

    -   Se *non* si segnala un problema specifico per il caricamento di una soluzione, provare ad attendere 5-10 minuti (o più, a seconda delle dimensioni della soluzione) dopo aver aperto la soluzione prima di registrare la traccia delle prestazioni. Il processo di caricamento della soluzione produce una grande quantità di dati, quindi l'attesa di alcuni minuti ci aiuta a concentrarci sul problema specifico che stai segnalando.

2.  Avviare una seconda copia di Visual Studio *senza soluzione aperta*

3.  Nella nuova copia di Visual Studio, aprire lo strumento **Segnala un problema**

4.  Seguire i passaggi descritti in [Segnala un problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) fino a raggiungere il passaggio "Fornire una traccia e un dump dell'heap (facoltativo).".

5.  Scegliere di registrare la prima copia di Visual Studio (quella che riscontra un problema di prestazioni) e avviare la registrazione.

    -   Apparirà l'applicazione Registrazione azioni utente e inizierà la registrazione.

    -   **Durante la registrazione,** eseguire l'azione problematica nella prima copia di Visual Studio. È difficile per noi correggere problemi di prestazioni specifici se non appaiono entro il tempo registrato.

    -   Se l'azione è più breve di 30 secondi e può essere ripetuta facilmente, ripetere l'azione per dimostrare ulteriormente il problema.

    -   Per la maggior parte dei casi, una traccia di 60 secondi è sufficiente per dimostrare i problemi, soprattutto se l'azione problematica è durata (o è stata ripetuta) per più di 30 secondi. La durata può essere regolata in base alle esigenze per acquisire il comportamento che si desidera venga risolto.

6.  Fare clic su "Stop Record" in Registrazione azioni non appena l'operazione lenta o l'evento della CPU elevata che si desidera segnalare è terminato. L'elaborazione della traccia delle prestazioni potrebbe richiedere alcuni minuti.

7.  Una volta completato, ci saranno diversi allegati al tuo feedback. Allegare eventuali file aggiuntivi che possono aiutare a riprodurre il problema (un progetto di esempio, screenshot, video, ecc.).

8.  Inviare il feedback.

Durante la registrazione di una traccia delle prestazioni, se l'operazione lenta o la CPU elevata che si sta segnalando termina, interrompere immediatamente la registrazione. Se vengono raccolte troppe informazioni, le informazioni meno recenti vengono sovrascritte. Se la traccia non viene arrestata a breve (entro pochi secondi) dopo l'operazione interessante, i dati di traccia utili verranno sovrascritti.

Non allegare direttamente le tracce delle prestazioni agli elementi di feedback esistenti nel sito Web della community di sviluppatori. La richiesta/fornitura di informazioni aggiuntive è un flusso di lavoro supportato nello strumento Report-a Problem incorporato in Visual Studio.Requesting/providing additional information is a supported workflow in Visual Studio's built-in Report a Problem tool. Se è necessaria una traccia delle prestazioni per risolvere un elemento di feedback precedente, imposteremo lo stato dell'elemento di feedback su "Necessita di ulteriori informazioni", che può essere risolto allo stesso modo della segnalazione di un nuovo problema. Per istruzioni dettagliate, fare riferimento alla sezione "Necessità di [ulteriori informazioni"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) nel documento dello strumento Segnala un problema.

> [!NOTE] 
> **Feedback più prezioso:** Per quasi tutti i problemi di lentezza / alta CPU, il feedback più prezioso è una\*descrizione di alto livello di ciò che si stava cercando di fare, insieme alla traccia delle prestazioni ( .etl.zip) che cattura il comportamento durante quel periodo.

**Tracce delle prestazioni avanzate**

Le funzionalità di raccolta delle tracce nello strumento Report-a-problem sono sufficienti per la maggior parte degli scenari. Ma ci sono momenti in cui è necessario un maggiore controllo sulla raccolta di tracce (ad esempio, traccia con una dimensione del buffer maggiore), nel qual caso PerfView è un ottimo strumento da utilizzare. Passaggi per la registrazione manuale della traccia delle prestazioni utilizzando lo strumento PerfView sono disponibili nella pagina Registrazione delle [tracce di prestazioni con PerfView.](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView)

## <a name="out-of-process-issues"></a>Problemi out-of-process

> [!NOTE]
> A partire da Visual Studio 2019 versione 16.3, i log out-of-process vengono automaticamente collegati ai commenti e suggerimenti inviati tramite lo strumento Segnala un problema. Tuttavia, se il problema è direttamente riproducibile, seguire i passaggi seguenti potrebbe comunque aiutare ad aggiungere ulteriori informazioni per diagnosticare meglio il problema.

Esistono diversi processi satellite che vengono eseguiti parallelamente a Visual Studio e forniscono varie funzionalità dall'esterno del processo principale di Visual Studio.There are a number of satellite processes that run parallel to Visual Studio and provide various features from outside of the main Visual Studio process. Se si verifica un errore in uno di questi processi satellite, viene in genere visualizzato sul lato Visual Studio come 'StreamJsonRpc.RemoteInvocationException' o 'StreamJsonRpc.ConnectionLostException'.

Ciò che rende questi tipi di problemi più utilizzabili è fornire registri aggiuntivi che possono essere raccolti attenendosi alla procedura seguente:

1.  Se si tratta di un problema riproducibile direttamente, iniziare eliminando la cartella **%temp%/servicehub/logs.** Se non è possibile riprodurre questo problema, mantenere intatta questa cartella e ignorare i seguenti punti elenco:

    -   Impostare la variabile di ambiente globale **ServiceHubTraceLevel** su **Tutti**
    -   Riprodurre il problema.

2.  Scaricare lo strumento di raccolta log di Microsoft Visual Studio e .NET Framework [qui](https://www.microsoft.com/download/details.aspx?id=12493).
3.  Eseguire lo strumento. In questo modo viene restituito un file zip in **%temp%/vslogs.zip**. Allegare il file al feedback.

## <a name="see-also"></a>Vedere anche

* [Opzioni per commenti e suggerimenti in Visual Studio](../ide/feedback-options.md)
* [Segnalare un problema con Visual Studio per Mac](/visualstudio/mac/report-a-problem)
* [Segnalare un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Community per sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/)
* [Privacy dei dati della community degli sviluppatori](developer-community-privacy.md)
