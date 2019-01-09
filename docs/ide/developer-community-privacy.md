---
title: Dati privati per segnalazioni di problemi
ms.date: 06/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c98747a4ad1d37d7a8b0d8cc51b4e1ddbd851663
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895766"
---
# <a name="developer-community-data-privacy"></a>Privacy dei dati della community degli sviluppatori

Per impostazione predefinita, tutte le informazioni contenute nelle segnalazioni di problemi nella [community degli sviluppatori](https://developercommunity.visualstudio.com/), inclusi eventuali commenti e risposte, sono visibili pubblicamente. Ciò rappresenta un vantaggio poiché consente all'intera community di visualizzare i problemi, le soluzioni ed eventuali soluzioni alternative individuate da altri utenti. Tuttavia sono disponibili opzioni che consentono di proteggere la privacy dei dati o dell'identità.

## <a name="identity-privacy"></a>Privacy dell'identità

Se non si vuole rivelare la propria identità, [creare un nuovo account Microsoft](https://signup.live.com/) che non divulghi informazioni dettagliate personali. Usare questo account per creare la segnalazione.

## <a name="data-privacy"></a>Privacy dei dati

Se si è preoccupati per la privacy dei dati, non inserire informazioni che si vogliono mantenere privati nel titolo o nel contenuto della segnalazione iniziale, che è sempre pubblica. Creare invece la segnalazione e si noti che i dettagli saranno inviati privatamente in un commento a parte. Dopo aver creato la segnalazione del problema, è possibile specificare chi può vedere le risposte e gli allegati:

1. Nella segnalazione creata scegliere **Aggiungi commento** per creare una descrizione privata del problema.

2. Nell'editor di risposta usare il controllo sotto i pulsanti **Invia** e **Annulla** per specificare chi potrà visualizzare la risposta. Scegliere **Viewable by moderators and the original poster** (Visualizzabile da moderatori e dall'autore originale del post) per limitare la visibilità ai dipendenti Microsoft e all'utente.

   ![Controllo della privacy per la community degli sviluppatori](media/developer-community-privacy-control.png)

   Solo le persone specificate potranno visualizzare il commento e le immagini, i collegamenti o il codice inclusi nello stesso. Tutte le risposte riportate sotto il commento hanno la stessa visibilità del commento originale anche se il controllo della privacy nelle risposte non visualizza correttamente lo stato di visibilità limitata.

3. Aggiungere la descrizione ed eventuali altre informazioni, immagini e allegati di file necessari per la procedura di riproduzione. Scegliere il pulsante **Invia** per inviare queste informazioni privatamente.

   > [!NOTE]
   > Esiste un limite di 2 GB per i file allegati e un massimo di 10 file. Se è necessario caricare un file di dimensioni maggiori, è possibile inviare una nuova segnalazione del problema o richiedere un URL di caricamento da un dipendente Microsoft in un commento privato.

Per garantire la privacy e assicurarsi che le informazioni riservate non siano visualizzabili pubblicamente, gestire sempre le interazioni con Microsoft in modo da rispondere usando un commento con visibilità limitata. Le risposte ad altri commenti potrebbero accidentalmente divulgare informazioni riservate.

## <a name="data-we-collect"></a>I dati raccolti

Se la **segnalazione del problema** viene avviata dal programma di installazione di Visual Studio, Microsoft raccoglie il log dell'installazione più recente.

Se la **segnalazione del problema** viene avviata da Visual Studio, Microsoft raccoglie uno o più dei seguenti tipi di dati:

- Voci Watson e .NET del log eventi

- File di log attività in memoria di Visual Studio

- File PerfWatson, se la raccolta Watson è abilitata, della cartella *VSFeedbackPerfWatsonData*

- File di log di LiveShare, se presenti, della cartella *VSFeedbackVSRTCLogs*

- File di log di Xamarin, se presenti, da *%LOCALAPPDATA%\Xamarin\Logs*

- File di log di NuGet, se presenti, da *%TEMP%\NuGetScratch\nuget-dg\nugetSpec.dg*

- File di log del debugger Web, se presenti:

   - *%TEMP%\vscode-chrome-debug.txt*

   - *%TEMP%\vscode-node-debug2.txt*

   - *%TEMP%\vscode-edge-debug.txt*

- Uno screenshot, se si sceglie di includerlo

- Registrazione dei dati, se si sceglie di includere una registrazione, che comprende:

   - Passi per riprodurre il problema

   - File di traccia ETL

   - File dump

    > [!NOTE]
    > È possibile eliminare i dati di registrazione che non si vogliono inviare prima di inviare la segnalazione.

## <a name="see-also"></a>Vedere anche

- [Come segnalare un problema con Visual Studio](how-to-report-a-problem-with-visual-studio-2017.md)
- [Segnalazioni e privacy](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)