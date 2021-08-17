---
title: Dati privati per segnalazioni di problemi
description: Informazioni su come mantenere i dati privati più sicuri quando si creano report sui problemi che gli sviluppatori Community esaminare.
ms.custom: SEO-VS-2020
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5ecfcbb6cf6e7681bfd68375f1e4b447c23fac83
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048999"
---
# <a name="developer-community-data-privacy"></a>Privacy dei dati della community degli sviluppatori

Per impostazione predefinita, tutte le informazioni contenute nelle segnalazioni di problemi nella [community degli sviluppatori](https://aka.ms/feedback/suggest?space=8), inclusi eventuali commenti e risposte, sono visibili pubblicamente. Ciò rappresenta un vantaggio poiché consente all'intera community di visualizzare i problemi, le soluzioni ed eventuali soluzioni alternative individuate da altri utenti. Tuttavia sono disponibili opzioni che consentono di proteggere la privacy dei dati o dell'identità.

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
   > Nel sito Community developer è previsto un limite di 2 GB per i file allegati e un massimo di 10 file. Se è necessario caricare un file di dimensioni maggiori, è possibile inviare una nuova segnalazione del problema o richiedere un URL di caricamento da un dipendente Microsoft in un commento privato.
   > Quando si chiude un problema, gli allegati associati verranno eliminati dopo 90 giorni.

Per garantire la privacy e assicurarsi che le informazioni riservate non siano visualizzabili pubblicamente, gestire sempre le interazioni con Microsoft in modo da rispondere usando un commento con visibilità limitata. Le risposte ad altri commenti potrebbero accidentalmente divulgare informazioni riservate.

## <a name="data-we-collect"></a>I dati raccolti

Se la **segnalazione del problema** viene avviata dal programma di installazione di Visual Studio, Microsoft raccoglie il log dell'installazione più recente.

Se la **segnalazione del problema** viene avviata da Visual Studio, Microsoft raccoglie uno o più dei seguenti tipi di dati:

- Voci Watson e .NET del log eventi

- File di log attività in memoria di Visual Studio

- File PerfWatson, se la raccolta Watson è abilitata

- File di log LiveShare, se esistenti

- File di log Xamarin, se esistenti

- File di log NuGet, se esistenti

- File di log del debugger Web, se esistenti

- Log di Service Hub e log degli errori MEF, se esistenti

- Log Python, se esistenti

- Log dell'editor Razor LSP, se presenti

- Windows Log dei moduli, se presenti

- Uno screenshot, se si sceglie di includerlo

- Registrazione dei dati, se si sceglie di includere una registrazione, che comprende:

  - Passi per riprodurre il problema

  - File di traccia ETL

  - File dump

> [!NOTE]
> I file di log, gli screenshot e la registrazione dei dati inviati possono aumentare significativamente la capacità di Microsoft di comprendere e rispondere al problema.  È quindi consigliabile includerli. Per proteggere la privacy, tutti i file di log allegati, gli screenshot e i dati di registrazione vengono inviati solo a Microsoft quando si fornisce l'autorizzazione inviando la segnalazione del problema con cui sono inclusi. È possibile visualizzare i file inclusi nel passaggio "Riepilogo" della finestra "Segnala un problema" prima di inviare il report. È possibile escludere i file di log di sistema dal report deselezionando "Collega log di sistema" nel passaggio "Riepilogo". Per informazioni di riferimento, vedere lo screenshot seguente. 
  > ![Segnalare un problema - Riepilogo dei log raccolti](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Vedi anche

- [Come segnalare un problema con Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [Segnalazioni e privacy](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
