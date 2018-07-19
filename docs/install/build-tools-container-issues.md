---
title: Problemi noti dei contenitori
description: I problemi noti seguenti possono verificarsi quando si installa Visual Studio Build Tools 2017 in un contenitore di Windows.
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06da94f4f2920aa7ce87822482a762a1451e9acb
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282496"
---
# <a name="known-issues-for-containers"></a>Problemi noti dei contenitori

Esistono alcuni problemi durante l'installazione di Visual Studio in un contenitore Docker.

## <a name="windows-container"></a>Contenitore di Windows

I problemi noti seguenti si verificano quando si installa Visual Studio Build Tools 2017 in un contenitore di Windows.

* Non è possibile installare Visual Studio in un contenitore basato sull'immagine microsoft/windowsservercore:10.0.14393.1593. Le immagini contrassegnate con versioni di Windows più recenti o precedenti dovrebbero funzionare.
* Non è possibile installare versioni di Windows SDK precedenti alla 10.0.14393. Alcuni pacchetti non vengono installati e i carichi di lavoro che dipendono da tali pacchetti non funzioneranno.
* Passare `-m 2GB` (o più) durante la compilazione dell'immagine. Alcuni carichi di lavoro richiedono più memoria rispetto al valore predefinito di 1 GB durante l'installazione.
* Configurare Docker per l'uso di dischi più grandi rispetto all'impostazione predefinita di 20 GB.
* Passare `--norestart` sulla riga di comando. Alla data di redazione di questo articolo, qualsiasi tentativo di riavviare un contenitore di Windows dall'interno del contenitore restituisce `ERROR_TOO_MANY_OPEN_FILES` all'host.
* Se si basa l'immagine direttamente su microsoft/windowsservercore, .NET Framework potrebbe non essere installato correttamente e non viene indicato alcun errore di installazione. Il codice gestito potrebbe non essere eseguito dopo il completamento dell'installazione. Basare invece l'immagine su [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) o versione successiva. Ad esempio, viene visualizzato un errore durante la compilazione con MSBuild come:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): errore MSB6003: non è stato possibile eseguire l'eseguibile dell'attività specificato "csc.exe". Impossibile caricare il file o l'assembly 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' o una delle relative dipendenze. Impossibile trovare il file specificato.

## <a name="build-tools-container"></a>Contenitore di Build Tools

Potrebbero verificarsi i seguenti problemi noti quando si usa un contenitore di Build Tools. Per scoprire se questi problemi sono stati corretti o se sono presenti altri problemi noti, visitare https://developercommunity.visualstudio.com.

* IntelliTrace potrebbe non funzionare in [alcuni scenari](https://github.com/Microsoft/vstest/issues/940) all'interno di un contenitore.

## <a name="get-support"></a>Supporto

Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:

* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto e trovare una risposta nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/).
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio). Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche

* [Installare Build Tools in un contenitore](build-tools-container.md)
* [Esempio avanzato per i contenitori](advanced-build-tools-container.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
