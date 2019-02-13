---
title: Problemi noti dei contenitori
description: I problemi noti seguenti possono verificarsi quando si installa Visual Studio Build Tools 2017 in un contenitore di Windows.
ms.date: 04/18/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f1fdfcc71f2bd17bf8ab4be0796350799af2c35
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935017"
---
# <a name="known-issues-for-containers"></a>Problemi noti dei contenitori

Esistono alcuni problemi durante l'installazione di Visual Studio in un contenitore Docker.

## <a name="windows-container"></a>Contenitore di Windows

I problemi noti seguenti si verificano quando si installa Visual Studio Build Tools 2017 in un contenitore di Windows.

* Non è possibile installare Visual Studio in un contenitore basato sull'immagine microsoft/windowsservercore:10.0.14393.1593. Le immagini contrassegnate con versioni di Windows precedenti o successive alla versione 10.0.14393 dovrebbero funzionare.
* Non è possibile installare versioni di Windows SDK precedenti alla versione 10.0.14393. Alcuni pacchetti non vengono installati e i carichi di lavoro che dipendono da tali pacchetti non funzioneranno.
* Passare `-m 2GB` (o più) durante la compilazione dell'immagine. Alcuni carichi di lavoro richiedono più memoria rispetto al valore predefinito di 1 GB durante l'installazione.
* Configurare Docker per l'uso di dischi più grandi rispetto all'impostazione predefinita di 20 GB.
* Passare `--norestart` sulla riga di comando. Alla data di redazione di questo articolo, qualsiasi tentativo di riavviare un contenitore di Windows dall'interno del contenitore restituisce `ERROR_TOO_MANY_OPEN_FILES` all'host.
* Se si basa l'immagine direttamente su microsoft/windowsservercore, .NET Framework potrebbe non essere installato correttamente e non viene indicato alcun errore di installazione. Il codice gestito potrebbe non essere eseguito dopo il completamento dell'installazione. Basare invece l'immagine su [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) o versione successiva. Ad esempio, viene visualizzato un errore durante la compilazione con MSBuild come:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): errore MSB6003: non è stato possibile eseguire il file eseguibile "csc.exe" dell'attività. Impossibile caricare il file o l'assembly 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' o una delle relative dipendenze. Impossibile trovare il file specificato.

* Non è possibile installare Visual Studio 2017 versione 15.8 o versioni precedenti (qualsiasi prodotto) in mcr<span></span>.microsoft.com/windows/servercore:1809 o versioni successive. Per altre informazioni, vedere https://aka.ms/setup/containers/servercore1809.

## <a name="build-tools-container"></a>Contenitore di Build Tools

Potrebbero verificarsi i seguenti problemi noti quando si usa un contenitore di Build Tools. Per scoprire se questi problemi sono stati corretti o se sono presenti altri problemi noti, visitare https://developercommunity.visualstudio.com.

* IntelliTrace potrebbe non funzionare in [alcuni scenari](https://github.com/Microsoft/vstest/issues/940) all'interno di un contenitore.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Build Tools in un contenitore](build-tools-container.md)
* [Esempio avanzato per i contenitori](advanced-build-tools-container.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
