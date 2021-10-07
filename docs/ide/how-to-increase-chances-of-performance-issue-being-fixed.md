---
title: Aumentare la probabilità che venga risolto un problema di prestazioni
description: Informazioni aggiuntive e procedure consigliate per l'invio di problemi di prestazioni in Visual Studio
ms.custom: SEO-VS-2020
author: madskristensen
ms.author: madsk
manager: jmartens
ms.technology: vs-ide-general
ms.date: 11/19/2019
ms.topic: conceptual
ms.openlocfilehash: c37f98198e999b1ab31bb6e371ca5b8700037736
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635327"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Come aumentare le probabilità di correzione di un problema di prestazioni

Lo strumento["Segnala un problema"](./how-to-report-a-problem-with-visual-studio.md?view=vs-2019&preserve-view=true)è ampiamente usato Visual Studio utenti per segnalare una serie di problemi. Il team Visual Studio le tendenze di arresto anomalo e lentezza nei commenti degli utenti e risolve i problemi che influiscono su un'ampia gamma di utenti. Maggiore è l'azione di un ticket di feedback specifico, maggiore è la probabilità che il ticket sia diagnosticato e risolto rapidamente dal team del prodotto. Questo documento descrive le procedure consigliate durante la segnalazione di problemi di arresto anomalo o lentezza per renderli più utilizzabili.

## <a name="general-best-practices"></a>Procedure consigliate generali

Visual Studio è una piattaforma complessa e di grandi dimensioni che supporta una vasta gamma di linguaggi, tipi di progetto, piattaforme e altro ancora. Le prestazioni sono una funzione dei componenti installati e attivi in una sessione, delle estensioni installate, delle impostazioni Visual Studio, della configurazione del computer e infine della forma del codice in corso di modifica. Dato il numero di variabili, è difficile stabilire se la segnalazione di problemi da un utente presenta lo stesso problema sottostante di un report di problema di un altro utente, anche se il sintomo visibile è lo stesso. Di seguito sono fornite alcune procedure consigliate per garantire che la segnalazione di problemi specifica abbia una maggiore probabilità di essere diagnosticata.

**Specificare il titolo più specifico possibile**

Cercare firme distinte per il problema segnalato e includere il più possibile nel titolo. Se il titolo è descrittivo, è meno probabile che gli utenti con problemi non correlati (ma  lo stesso sintomo superficiale) voteranno o commenteranno il ticket, rendendo così più difficile la diagnosi del problema.

**In caso di dubbi, registrare un nuovo report di problema**

Molti problemi potrebbero non avere alcuna firma distintiva o passaggi da riprodurre. In questi casi, un nuovo report è migliore di un upvote o di un commento su un altro report, che segnala un sintomo esterno *simile.* A seconda del tipo di report, includere file di diagnostica aggiuntivi per il report, come descritto più avanti in questo documento.

**Procedure consigliate specifiche del problema**

Di seguito sono descritti i problemi difficili da diagnosticare senza buoni file di diagnostica. Dopo aver identificato il caso che meglio descrive il problema, seguire la procedura di feedback specifica per tale caso.

- [Arresti anomali:](#crashes) Un arresto anomalo si verifica quando il processo (Visual Studio) termina in modo imprevisto.

- [Non risponde:](#unresponsiveness) Vs non risponde per un lungo periodo di tempo.

- [Problemi di lentezza:](#slowness-and-high-cpu-issues) Qualsiasi azione specifica in Visual Studio è più lenta del desiderato

- [CPU elevata:](#slowness-and-high-cpu-issues) Periodi estesi di utilizzo imprevisto elevato della CPU

- [Problemi out-of-process:](#out-of-process-issues) Un problema causato da un Visual Studio satellite

## <a name="crashes"></a>Crashes
Un arresto anomalo si verifica quando il processo (Visual Studio) termina in modo imprevisto.

**Arresti anomali riproducibili direttamente**

Gli arresti anomali riproducibili direttamente sono casi con tutte le caratteristiche seguenti:

- È possibile osservare seguendo un set noto di passaggi

- Può essere osservato in più computer (se disponibile)

- Può essere riprodotto nel codice di esempio o in un progetto che può essere collegato o fornito come parte del feedback (se la procedura prevede l'apertura di un progetto o di un documento)

Per questi problemi, seguire la procedura descritta in "[Come segnalare un problema](./how-to-report-a-problem-with-visual-studio.md)" e assicurarsi di includere:

- Procedura per riprodurre il problema

- Un progetto di riproduzione autonomo come descritto in precedenza. Se la riproduzione autonoma non è possibile, includere:

  - Linguaggio dei progetti aperti \# (C, C++ e così via)

  - Tipo di progetto (applicazione console, ASP.NET e così via)

> [!NOTE]
> **Feedback più prezioso:** In questo caso, il feedback più utile è il set di passaggi per riprodurre il problema insieme al codice sorgente di esempio.

**Arresti anomali sconosciuti**

Se non si è certi di ciò che causa gli arresti anomali o sembrano casuali, è possibile acquisire i dump in locale ogni volta che Visual Studio si arresta in modo anomalo e associarli a elementi di feedback separati. Per salvare i dump in locale quando Visual Studio si arresta in modo anomalo, eseguire i comandi seguenti in una finestra di comando dell'amministratore:

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

Personalizzare il numero di dump e la cartella dump in base alle esigenze. Altre informazioni su queste impostazioni sono [disponibili qui.](/windows/win32/wer/collecting-user-mode-dumps)

> [!NOTE]
> I dump acquisiti usando Gestione attività sono probabilmente di un bitness errato, il che li rende meno utilizzabili. La procedura descritta in precedenza è il modo preferito per l'acquisizione di un dump dell'heap. Se si vuole usare Gestione attività, chiudere quello attualmente in esecuzione, avviare il Gestione attività a 32 bit (%windir% syswow64taskmgr.exe) e raccogliere un \\ dump dell'heap. \\

> [!NOTE]
> Ogni file di dump prodotto da questo metodo avrà dimensioni massime di 4 GB. Assicurarsi di impostare DumpFolder su un percorso con spazio su disco adeguato o modificare DumpCount in modo appropriato.

Ogni volta Visual Studio si arresta in modo anomalo, verrà creato un file di dump **devenv.exe.[ number].dmp** nel percorso configurato.

Usare quindi il Visual Studio "Segnala un problema..." Funzionalità. Consentirà di collegare il dump appropriato.

1. Individuare il file dump per l'arresto anomalo del sistema segnalato (cercare un file con l'ora di creazione corretta)

2. Se possibile, comprimere il file \* (.zip) per ridurne le dimensioni prima di inviare commenti e suggerimenti

3. Seguire la procedura descritta in "[How to Report a Problem](./how-to-report-a-problem-with-visual-studio.md)" (Come segnalare un problema) e collegare il dump dell'heap a un nuovo elemento di feedback.

> [!NOTE]
> **Feedback più prezioso:** In questo caso, il feedback più utile è il dump dell'heap acquisito al momento dell'arresto anomalo.

## <a name="unresponsiveness"></a>Apatia
Vs non risponde per un lungo periodo di tempo.

**Unresponsiveness riproducibile direttamente**

Come descritto nella sezione corrispondente sugli arresti anomali, per i problemi facilmente riproducibili, visibili su più computer e dimostrabili in un piccolo esempio, i report di feedback più preziosi sono quelli che includono passaggi per riprodurre il problema e includono codice sorgente di esempio che illustra il problema.

**Non risponde sconosciuto**

Se un non risponde si manifesta in modo imprevedibile, all'occorrenza successiva avviare una nuova istanza di Visual Studio e segnalare un problema da tale istanza.
Nella schermata "Record" assicurarsi di selezionare la Visual Studio sessione che non risponde. Per altre informazioni su come registrare le azioni che è possibile seguire per riprodurre il problema, vedere Passaggio 8 nella pagina Come segnalare [un](./how-to-report-a-problem-with-visual-studio.md) problema.

Se l Visual Studio istanza che non risponde è stata avviata in modalità amministratore, anche la seconda istanza deve essere avviata in modalità amministratore.

>[!NOTE]
> **Feedback più prezioso:** In questo caso, il feedback più utile è il dump dell'heap acquisito al momento dell'annullamento della risposta.

## <a name="slowness-and-high-cpu-issues"></a>Lentezza e problemi di CPU elevati

Ciò che rende più fattibile un problema di lentezza o utilizzo elevato della CPU è una traccia delle prestazioni acquisita mentre è in corso l'operazione lenta o un evento elevato della CPU.

>[!NOTE]
> Quando possibile, isolare ogni scenario in un report di feedback separato e specifico.
Ad esempio, se la digitazione e la navigazione sono entrambe lente, seguire questa procedura una sola volta per ogni problema. Ciò consente al team del prodotto di isolare la causa di problemi specifici.

Per ottenere risultati ottimali nell'acquisizione delle prestazioni, seguire questa procedura:

1. Se non è già in esecuzione, aprire una copia Visual Studio in cui riprodurre il problema

    - Configurare tutti gli elementi per riprodurre il problema. Ad esempio, se è necessario caricare un progetto specifico con un file specifico aperto, assicurarsi che entrambi i passaggi siano completi prima di procedere.

    - Se non  si segnala un problema specifico per il caricamento di una soluzione, provare ad attendere da 5 a 10 minuti (o più, a seconda delle dimensioni della soluzione) dopo aver aperto la soluzione prima di registrare la traccia delle prestazioni. Il processo di caricamento della soluzione produce una grande quantità di dati, quindi l'attesa di alcuni minuti consente di concentrarsi sul problema specifico segnalato.

2. Avviare una seconda copia del Visual Studio *senza soluzione aperta*

3. Nella nuova copia di Visual Studio aprire lo strumento **Segnala** un problema

4. Seguire la procedura descritta in [Come segnalare un problema](./how-to-report-a-problem-with-visual-studio.md) fino a raggiungere il passaggio "Fornire un dump di traccia e heap (facoltativo)".

5. Scegliere di registrare la prima copia del Visual Studio (quella in cui si è verificato un problema di prestazioni) e avviare la registrazione.

    - Verrà visualizzata l'applicazione Steps Recorder e verrà avviata la registrazione.

    - **Durante la registrazione,** eseguire l'azione problematica nella prima copia del Visual Studio. È difficile correggere specifici problemi di prestazioni se non vengono visualizzati entro il tempo registrato.

    - Se l'azione è più breve di 30 secondi e può essere ripetuta facilmente, ripetere l'azione per dimostrare ulteriormente il problema.

    - Nella maggior parte dei casi, è sufficiente una traccia di 60 secondi per dimostrare i problemi, soprattutto se l'azione problematica è durata (o è stata ripetuta) per più di 30 secondi. La durata può essere modificata in base alle esigenze per acquisire il comportamento desiderato.

6. Fare clic su "Arresta record" in Registrazione passaggi non appena l'operazione lenta o l'evento cpu elevato da segnalare sono stati completati. L'elaborazione della traccia delle prestazioni può richiedere alcuni minuti.

7. Al termine, saranno disponibili diversi allegati ai commenti e suggerimenti. Allegare eventuali file aggiuntivi che consentono di riprodurre il problema (un progetto di esempio, screenshot, video e così via).

8. Inviare il feedback.

Durante la registrazione di una traccia delle prestazioni, se l'operazione lenta o la CPU elevata segnalata termina, arrestare immediatamente la registrazione. Se vengono raccolte troppe informazioni, le informazioni meno recenti vengono sovrascritte. Se la traccia non viene arrestata subito (entro pochi secondi) dopo l'operazione interessante, i dati di traccia utili verranno sovrascritti.

Non collegare direttamente tracce delle prestazioni agli elementi di feedback esistenti nel sito Web Community developer. Richiedere/fornire informazioni aggiuntive è un flusso di lavoro supportato Visual Studio strumento predefinito Segnala un problema. Se è necessaria una traccia delle prestazioni per risolvere un elemento di feedback precedente, lo stato dell'elemento di feedback verrà impostato su "Need More Info", che può essere risposto allo stesso modo in cui viene segnalato un nuovo problema. Per istruzioni dettagliate, vedere la sezione ["Servono altre informazioni"](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed) nel documento dello strumento Segnala un problema.

> [!NOTE]
> **Commenti e suggerimenti più importanti:** Per quasi tutti i problemi di lentezza/utilizzo elevato della CPU, il feedback più utile è una descrizione di alto livello delle operazioni che si stava tentando di eseguire, insieme alla traccia delle prestazioni (.etl.zip) che acquisisce il comportamento durante tale \* periodo.

**Tracce avanzate delle prestazioni**

Le funzionalità di raccolta delle tracce nello strumento Segnala un problema sono sufficienti per la maggior parte degli scenari. In alcuni casi, tuttavia, è necessario un maggiore controllo sulla raccolta di tracce(ad esempio, traccia con dimensioni del buffer maggiori), nel qual caso PerfView è un ottimo strumento da usare. I passaggi per la registrazione manuale della traccia delle prestazioni con lo strumento PerfView sono disponibili nella pagina Registrazione delle tracce [delle prestazioni con PerfView.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Recording-performance-traces-with-PerfView.md)

## <a name="out-of-process-issues"></a>Problemi out-of-process

> [!NOTE]
> A partire Visual Studio 2019 versione 16.3, i log out-of-process vengono allegati automaticamente ai commenti e suggerimenti inviati usando lo strumento Segnala un problema.
Tuttavia, se il problema è riproducibile direttamente, la procedura seguente potrebbe comunque contribuire ad aggiungere altre informazioni per facilitare la diagnosi del problema.

Esistono diversi processi satellite che vengono eseguiti in parallelo Visual Studio e forniscono varie funzionalità dall'esterno del processo Visual Studio principale. Se si verifica un errore in uno di questi processi satellite, viene in genere visualizzato sul lato Visual Studio come 'StreamJsonRpc.RemoteInvocationException' o 'StreamJsonRpc.ConnectionLostException'.

Ciò che rende questi tipi di problemi più utilizzabili è fornire log aggiuntivi che possono essere raccolti seguendo questa procedura:

1. Se si tratta di un problema riproducibile direttamente, iniziare eliminando la cartella **%temp%/servicehub/logs.** Se non è possibile riprodurre questo problema, mantenere intatta questa cartella e ignorare i punti elenco seguenti:

    - Impostare la variabile di ambiente globale **ServiceHubTraceLevel** su **All**
    - Riprodurre il problema.

2. Scaricare lo strumento Microsoft Visual Studio e .NET Framework Log Collection Tool [qui](https://www.microsoft.com/download/details.aspx?id=12493).
3. Eseguire lo strumento. Verrà restituito un file ZIP in **%temp%/vslogs.zip**. Allegare il file al feedback.

## <a name="see-also"></a>Vedi anche

* [Segnalare un problema con Visual Studio per Mac](/visualstudio/mac/report-a-problem)
* [Segnalare un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Developer Community](https://developercommunity.visualstudio.com/home)
* [Privacy dei dati della community degli sviluppatori](developer-community-privacy.md)