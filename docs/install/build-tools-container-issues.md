---
title: Problemi noti dei contenitori | Microsoft Docs
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 75825d368d0098c466c44a23fa18ac1af7b06e64
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2017
---
# <a name="known-issues-for-containers"></a>Problemi noti dei contenitori

Esistono alcuni problemi durante l'installazione di Visual Studio in un contenitore Docker.

## <a name="windows-container"></a>Contenitore di Windows

I problemi noti seguenti si verificano quando si installa Visual Studio Build Tools 2017 in un contenitore di Windows.

* Non è possibile installare Visual Studio in un contenitore basato sull'immagine microsoft/windowsservercore:10.0.14393.1593. Le immagini contrassegnate con versioni di Windows più recenti o precedenti dovrebbero funzionare.
* Non è possibile installare versioni di Windows SDK precedenti alla 10.0.14393. Alcuni pacchetti non vengono installati e i carichi di lavoro che dipendono da tali pacchetti non funzioneranno.
* È necessario passare `-m 2GB` (o più) durante la compilazione dell'immagine. Alcuni carichi di lavoro richiedono più memoria rispetto al valore predefinito di 1 GB durante l'installazione.
* È necessario configurare Docker per l'uso si dischi più grandi rispetto all'impostazione predefinita di 20 GB.
* È necessario passare `--norestart` nella riga di comando. Alla data di redazione di questo articolo, qualsiasi tentativo di riavviare un contenitore di Windows dall'interno del contenitore restituisce `ERROR_TOO_MANY_OPEN_FILES` all'host.

## <a name="build-tools-container"></a>Contenitore di Build Tools

Potrebbero verificarsi i seguenti problemi noti quando si usa un contenitore di Build Tools. Per scoprire se questi problemi sono stati corretti o se sono presenti altri problemi noti, visitare https://developercommunity.visualstudio.com.

* IntelliTrace potrebbe non funzionare in [alcuni scenari](https://github.com/Microsoft/vstest/issues/940) all'interno di un contenitore.

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce,per suggerimenti per la risoluzione dei problemi vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). È anche possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) nell'IDE di Visual Studio o condividere un suggerimento su [UserVoice](https://visualstudio.uservoice.com/forums/121579). È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte. È anche possibile comunicare con Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio) (è necessario un account [GitHub](https://github.com/)).

## <a name="see-also"></a>Vedere anche

* [Installare Build Tools in un contenitore](build-tools-container.md)
* [Esempio avanzato per i contenitori](advanced-build-tools-container.md)
