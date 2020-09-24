---
title: Aumentare la probabilità di correzione di un problema di prestazioni
description: Informazioni aggiuntive e procedure consigliate per l'invio di problemi di prestazioni in Visual Studio
ms.custom: SEO-VS-2020
author: madskristensen
ms.author: madsk
manager: jillfra
ms.date: 11/19/2019
ms.topic: conceptual
ms.openlocfilehash: 1567e75d5e0a6f27aee68cd783b9ebd4a70815f4
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211188"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Come aumentare le probabilità di correzione di un problema di prestazioni

Lo strumento "[segnala un problema](./how-to-report-a-problem-with-visual-studio.md?view=vs-2019&preserve-view=true)" è ampiamente usato dagli utenti di Visual Studio per segnalare una serie di problemi. Il team di Visual Studio individua tendenze di arresto anomalo e lentezza nei commenti degli utenti e risolve problemi che influiscano su una vasta gamma di utenti. Il ticket di feedback specifico è più praticabile, più probabilmente verrà diagnosticato e risolto rapidamente dal team del prodotto. Questo documento descrive le procedure consigliate durante la segnalazione di problemi di arresto anomalo o lentezza per renderli più interoperabili.

## <a name="general-best-practices"></a>Procedure consigliate generali

Visual Studio è una piattaforma complessa e di grandi dimensioni che supporta numerosi linguaggi, tipi di progetto, piattaforme e altro ancora. Il modo in cui viene eseguito è una funzione in cui i componenti vengono installati e attivati in una sessione, le estensioni installate, le impostazioni di Visual Studio, la configurazione del computer e infine la forma del codice in corso di modifica. Dato il numero di variabili, è difficile stabilire se il rapporto del problema di un utente presenta lo stesso problema sottostante di un problema segnalato da un altro utente, anche se il sintomo visibile è lo stesso. Di seguito sono riportate alcune procedure consigliate per garantire che il report specifico del problema abbia una maggiore probabilità di essere diagnosticato.

**Fornire il titolo più specifico possibile**

Cercare firme distinte per il problema segnalato e includere quanto più possibile nel titolo. Se il titolo è descrittivo, è meno probabile che gli utenti con problemi non correlati, ma con lo stesso sintomo superficiale, votino o commentino sul ticket, rendendo quindi *la* diagnosi del problema più difficile.

**In caso di dubbi, registrare un nuovo report di problemi**

Molti problemi potrebbero non avere alcuna firma o procedura distinta per la riproduzione. In questi casi, un nuovo report è migliore di un voto o un commento su un altro report, che segnala un *sintomo*esterno simile. A seconda del tipo di report, includere i file di diagnostica aggiuntivi nel report, come descritto più avanti in questo documento.

**Procedure consigliate specifiche per i problemi**

Di seguito sono descritti i problemi difficili da diagnosticare senza file di diagnostica validi. Dopo aver identificato il caso che meglio descrive il problema, seguire i passaggi di feedback specifici per questo caso.

- [Arresti anomali:](#crashes) Si verifica un arresto anomalo quando il processo (Visual Studio) termina in modo imprevisto.

- Non [risposta:](#unresponsiveness) VS smette di rispondere per un lungo periodo di tempo.

- [Problemi di lentezza:](#slowness-and-high-cpu-issues) Qualsiasi azione specifica in Visual Studio è più lenta di quella desiderata

- [CPU elevata:](#slowness-and-high-cpu-issues) Periodi prolungati di utilizzo elevato della CPU inaspettatamente

- [Problemi out-of-process:](#out-of-process-issues) Un problema causato da un processo satellite di Visual Studio

## <a name="crashes"></a>Crashes
Si verifica un arresto anomalo quando il processo (Visual Studio) termina in modo imprevisto.

**Arresti anomali direttamente riproducibili**

Gli arresti anomali direttamente riproducibili sono casi con le seguenti caratteristiche:

- Può essere osservato seguendo un set di passaggi noto

- Può essere osservato su più computer (se disponibili)

- Può essere riprodotto nel codice di esempio o in un progetto che può essere collegato o fornito come parte del feedback (se i passaggi implicano l'apertura di un progetto o di un documento)

Per questi problemi, attenersi alla procedura descritta in "[come segnalare un problema](./how-to-report-a-problem-with-visual-studio.md)" e assicurarsi di includere:

- Passaggi per riprodurre il problema

- Un progetto di ripetizione autonomo, come descritto in precedenza. Se non è possibile eseguire la ripetizione autonoma, includere:

  - Lingua dei progetti aperti (C \# , C++ e così via)

  - Il tipo di progetto (applicazione console, ASP.NET e così via)

> [!NOTE]
> **Feedback più prezioso:** Per questo caso, il feedback più prezioso è la serie di passaggi per riprodurre il problema insieme al codice sorgente di esempio.

**Arresti anomali sconosciuti**

Se non si è certi della causa degli arresti anomali o sembrano casuali, è possibile acquisire i dump localmente a ogni arresto anomalo di Visual Studio e alleghirli a elementi di feedback distinti. Per salvare i dump localmente quando si verifica un arresto anomalo di Visual Studio, eseguire i comandi seguenti in una finestra di comando amministratore:

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

Personalizzare il numero di dump e la cartella dump nel modo appropriato. Altre informazioni su queste impostazioni sono disponibili [qui](/windows/win32/wer/collecting-user-mode-dumps).

> [!NOTE]
> È probabile che i dump acquisiti tramite Gestione attività siano di bit errato, rendendoli meno utilizzabili. La procedura descritta in precedenza è il modo migliore per acquisire un dump dell'heap. Se si vuole usare Gestione attività, chiudere quella attualmente in esecuzione, avviare Gestione attività a 32 bit (% windir% \\ syswow64 \\taskmgr.exe) e raccogliere un dump dell'heap da questa posizione.

> [!NOTE]
> Ogni file di dump prodotto da questo metodo avrà dimensioni massime di 4 GB. Assicurarsi di impostare DumpFolder su un percorso con spazio su disco sufficiente o di regolare il DumpCount in modo appropriato.

Ogni volta che si verifica un arresto anomalo di Visual Studio, viene creato un file dump **devenv.exe. [ numero] file. dmp** nel percorso configurato.

Quindi, usare "segnala un problema" di Visual Studio. funzionalità. Consente di alleghiare il dump appropriato.

1. Individuare il file di dump per l'arresto anomalo che si sta segnalando (cercare un file con l'ora di creazione corretta)

2. Se possibile, comprimere il file ( \* zip) per ridurne le dimensioni prima di inviare commenti e suggerimenti

3. Attenersi alla procedura descritta in "[come segnalare un problema](./how-to-report-a-problem-with-visual-studio.md)" e alleghi il dump dell'heap a un nuovo elemento di feedback.

> [!NOTE]
> **Feedback più prezioso:** Per questo caso, il feedback più prezioso è il dump dell'heap acquisito al momento dell'arresto anomalo.

## <a name="unresponsiveness"></a>Blocco
VS smette di rispondere per un lungo periodo di tempo.

**Non risponde direttamente riproducibili**

Come descritto nella sezione corrispondente sugli arresti anomali, per i problemi che possono essere facilmente riprodotti, visualizzati in più computer e possono essere illustrati in un piccolo esempio, i report di feedback più preziosi sono quelli che includono i passaggi per riprodurre il problema e includono il codice sorgente di esempio che illustra il problema.

**Non risposta sconosciuta**

Se una mancata risposta si manifesta in modo imprevedibile, all'occorrenza successiva avviare una nuova istanza di Visual Studio e segnalare un problema da tale istanza.
Nella schermata "record" assicurarsi di selezionare la sessione di Visual Studio che non risponde. Per ulteriori informazioni su come registrare le azioni che è possibile eseguire per riprodurre il problema, vedere il passaggio 8 sulla pagina [come segnalare un problema](./how-to-report-a-problem-with-visual-studio.md) .

Se l'istanza di Visual Studio che non risponde è stata avviata in modalità amministratore, anche la seconda istanza deve essere avviata in modalità amministratore.

>[!NOTE]
> **Feedback più prezioso:** Per questo caso, il feedback più prezioso è il dump dell'heap acquisito al momento della mancata risposta.

## <a name="slowness-and-high-cpu-issues"></a>Lentezza e problemi di CPU elevati

Ciò che rende più praticabile un problema di lentezza o un utilizzo elevato della CPU è una traccia delle prestazioni acquisita mentre è in corso l'operazione lenta o un evento CPU elevato.

>[!NOTE]
> Quando possibile, isolare ogni scenario in un report separato specifico di feedback.
Se, ad esempio, la digitazione e la navigazione sono entrambe lente, attenersi alla procedura seguente una volta per ogni problema. Questo consente al team del prodotto di isolare la cause di problemi specifici.

Per ottenere risultati ottimali nell'acquisizione delle prestazioni, attenersi alla procedura seguente:

1. Se non è già in esecuzione, è possibile aprire una copia di Visual Studio in cui riprodurre il problema

    - Configurare tutti gli elementi per riprodurre il problema. Ad esempio, se è necessario caricare un particolare progetto con un file specifico aperto, assicurarsi che entrambi i passaggi siano completi prima di procedere.

    - Se *non* si segnala un problema specifico per il caricamento di una soluzione, provare ad attendere 5-10 minuti (o più, a seconda delle dimensioni della soluzione) dopo aver aperto la soluzione prima di registrare la traccia delle prestazioni. Il processo di caricamento della soluzione produce una grande quantità di dati, pertanto l'attesa di alcuni minuti ci consente di concentrarsi sul problema specifico che si sta segnalando.

2. Avvia una seconda copia di Visual Studio *senza alcuna soluzione aperta*

3. Nella nuova copia di Visual Studio aprire lo strumento **segnala un problema**

4. Seguire i passaggi descritti in [come segnalare un problema](./how-to-report-a-problem-with-visual-studio.md) fino a raggiungere il passaggio "fornire una traccia e un dump di heap (facoltativo)".

5. Scegliere di registrare la prima copia di Visual Studio (un problema di prestazioni) e avviare la registrazione.

    - Viene visualizzata l'applicazione Steps Recorder e viene avviata la registrazione.

    - **Durante la registrazione,** eseguire l'azione problematica nella prima copia di Visual Studio. È difficile correggere problemi di prestazioni specifici se non vengono visualizzati nell'intervallo di tempo registrato.

    - Se l'azione è inferiore a 30 secondi e può essere facilmente ripetuta, ripetere l'azione per illustrare ulteriormente il problema.

    - Per la maggior parte dei casi, una traccia di 60 secondi è sufficiente per illustrare i problemi, soprattutto se l'azione problematica è durata (o è stata ripetuta) per più di 30 secondi. La durata può essere modificata in modo da acquisire il comportamento che si desidera correggere.

6. Fare clic su "Interrompi record" nella registrazione passaggi non appena viene completata l'operazione lenta o l'evento CPU elevato da segnalare. Potrebbero essere necessari alcuni minuti per elaborare la traccia delle prestazioni.

7. Al termine, saranno presenti diversi allegati ai commenti. Alleghi eventuali file aggiuntivi che possono contribuire a riprodurre il problema (un progetto di esempio, schermate, video e così via).

8. Inviare il feedback.

Durante la registrazione di una traccia delle prestazioni, se l'operazione lenta o la CPU elevata che si sta segnalando viene portata a termine, arrestare immediatamente la registrazione. Se viene raccolta una quantità eccessiva di informazioni, le informazioni meno recenti vengono sovrascritte. Se la traccia non viene interrotta a breve (entro pochi secondi) dopo l'operazione interessante, i dati di traccia utili vengono sovrascritti.

Non alleghi direttamente le tracce delle prestazioni agli elementi di feedback esistenti nel sito Web della community degli sviluppatori. La richiesta o la fornitura di informazioni aggiuntive è un flusso di lavoro supportato nello strumento di segnalazione del problema predefinito di Visual Studio. Se è necessaria una traccia delle prestazioni per risolvere un elemento di feedback precedente, lo stato dell'elemento feedback verrà impostato su "need more info", che può essere risposto allo stesso modo in cui viene segnalato un nuovo problema. Per istruzioni dettagliate, vedere la [sezione "need more info"](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed) nel documento di report di un problema.

> [!NOTE]
> **Feedback più prezioso:** Per quasi tutti i problemi di rallentamento/CPU elevato, il feedback più prezioso è una descrizione di alto livello di ciò che si stava tentando di eseguire, insieme alla traccia delle prestazioni ( \*.etl.zip) che acquisisce il comportamento durante tale periodo di tempo.

**Tracce di prestazioni avanzate**

Per la maggior parte degli scenari, le funzionalità di raccolta delle tracce nello strumento segnala un problema sono sufficienti. In alcuni casi, tuttavia, è necessario un maggiore controllo sulla raccolta di tracce (ad esempio, traccia con dimensioni del buffer maggiori), nel qual caso PerfView è un ottimo strumento da usare. I passaggi per la registrazione manuale della traccia delle prestazioni con lo strumento PerfView sono reperibili nella pagina [registrazione delle tracce delle prestazioni con PerfView](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Recording-performance-traces-with-PerfView.md) .

## <a name="out-of-process-issues"></a>Problemi out-of-process

> [!NOTE]
> A partire da Visual Studio 2019 versione 16,3, i log out-of-process vengono collegati automaticamente ai commenti inviati usando lo strumento segnala un problema.
Tuttavia, se il problema è direttamente riproducibile, la procedura seguente potrebbe ancora aiutare ad aggiungere ulteriori informazioni per facilitare la diagnosi del problema.

Sono disponibili numerosi processi satellite che vengono eseguiti in parallelo a Visual Studio e forniscono varie funzionalità dall'esterno del processo principale di Visual Studio. Se si verifica un errore in uno di questi processi satellite, viene in genere visualizzato sul lato di Visual Studio come ' StreamJsonRpc. RemoteInvocationException ' o ' StreamJsonRpc. ConnectionLostException '.

Ciò che rende più praticabile questi tipi di problemi consiste nel fornire log aggiuntivi che possono essere raccolti attenendosi alla procedura seguente:

1. Se si tratta di un problema direttamente riproducibile, iniziare eliminando la cartella **% Temp%/servicehub/logs** . Se non è possibile riprodurre questo problema, mantenere intatta la cartella e ignorare i punti elenco seguenti:

    - Imposta la variabile di ambiente globale **ServiceHubTraceLevel** su **All**
    - Riprodurre il problema.

2. Scaricare lo strumento di raccolta dei log Microsoft Visual Studio e .NET Framework [qui](https://www.microsoft.com/download/details.aspx?id=12493).
3. Eseguire lo strumento. Viene restituito un file zip a **% Temp%/vslogs.zip**. Alleghi il file ai tuoi commenti.

## <a name="see-also"></a>Vedere anche

* [Opzioni per commenti e suggerimenti in Visual Studio](../ide/feedback-options.md)
* [Segnala un problema con Visual Studio per Mac](/visualstudio/mac/report-a-problem)
* [Segnalare un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/)
* [Privacy dei dati della community degli sviluppatori](developer-community-privacy.md)