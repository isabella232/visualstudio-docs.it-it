---
title: Problemi noti dei contenitori
description: I problemi noti seguenti possono verificarsi quando si installa Visual Studio Build Tools in un contenitore di Windows.
ms.date: 07/03/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2433f18f9980657ced5f5ddb274f5aa2a7671a60
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888607"
---
# <a name="known-issues-for-containers"></a>Problemi noti dei contenitori

Esistono alcuni problemi durante l'installazione di Visual Studio in un contenitore Docker.

## <a name="windows-container"></a>Contenitore di Windows

I problemi noti seguenti si verificano quando si installa Visual Studio Build Tools in un contenitore di Windows.

::: moniker range="vs-2017"

* Non è possibile installare Visual Studio in un contenitore basato sull'immagine microsoft/windowsservercore:10.0.14393.1593. Le immagini contrassegnate con versioni di Windows precedenti o successive alla versione 10.0.14393 dovrebbero funzionare.

* Non è possibile installare versioni di Windows SDK precedenti alla versione 10.0.14393. Alcuni pacchetti non vengono installati e i carichi di lavoro che dipendono da tali pacchetti non funzioneranno.

::: moniker-end

* Passare `-m 2GB` (o più) durante la compilazione dell'immagine. Alcuni carichi di lavoro richiedono più memoria rispetto al valore predefinito di 1 GB durante l'installazione.
* Configurare Docker per l'uso di dischi più grandi rispetto all'impostazione predefinita di 20 GB.
* Passare `--norestart` sulla riga di comando. Alla data di redazione di questo articolo, qualsiasi tentativo di riavviare un contenitore di Windows dall'interno del contenitore restituisce `ERROR_TOO_MANY_OPEN_FILES` all'host.
* Se si basa l'immagine direttamente su microsoft/windowsservercore, .NET Framework potrebbe non essere installato correttamente e non viene segnalato nessun errore di installazione. Il codice gestito potrebbe non essere eseguito dopo il completamento dell'installazione. Basare invece l'immagine su [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) o versione successiva. Ad esempio, durante la compilazione con MSBuild potrebbe essere visualizzato un errore simile al seguente:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): errore MSB6003: non è stato possibile eseguire l'eseguibile dell'attività specificato "csc.exe". Impossibile caricare il file o l'assembly 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' o una delle relative dipendenze. Impossibile trovare il file specificato.

::: moniker range="vs-2017"

* Non è possibile installare Visual Studio 2017 versione 15.8 o versioni precedenti (qualsiasi prodotto) in mcr.microsoft.com/windows/servercore:1809 o versioni successive. Per altre informazioni, vedere https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Contenitore di Build Tools

Potrebbero verificarsi i seguenti problemi noti quando si usa un contenitore di Build Tools. Per scoprire se questi problemi sono stati corretti o se sono presenti altri problemi noti, visitare https://developercommunity.visualstudio.com.

* IntelliTrace potrebbe non funzionare in [alcuni scenari](https://github.com/Microsoft/vstest/issues/940) all'interno di un contenitore.
* Nelle versioni precedenti di Docker per Windows, le dimensioni dell'immagine del contenitore predefinite sono solo di 20 GB e non saranno abbastanza per Build Tools. Seguire le [istruzioni per modificare le dimensioni dell'immagine](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) specificando minimo 127 GB.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Build Tools in un contenitore](build-tools-container.md)
* [Esempio avanzato per i contenitori](advanced-build-tools-container.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
