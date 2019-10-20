---
title: Un processo ha rilevato un errore irreversibile
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fae832cf62b2cfc6302289352bc5a2f2afb9f13
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667054"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Errore irreversibile del processo di Visual Studio

Visual Studio usa diversi processi out-of-process per svolgere le attività necessarie in background, ad esempio testing unità in tempo reale, analizzatori di codice e altro ancora. Questi processi vengono eseguiti out-of-process per offrire vantaggi in termini di prestazioni di Visual Studio, consentendo ad esempio a Visual Studio di rispondere più rapidamente durante l'esecuzione di processi lunghi e con uso intensivo di risorse. E poiché Visual Studio è un processo a 32 bit, l'esecuzione di processi out-of-process rende disponibile uno spazio di memoria più grande dove svolgere le attività con uso intensivo della memoria.

Se il processo *ServiceHub.RoslynCodeAnalysisService.exe* o *ServiceHub.RoslynCodeAnalysisService32.exe* termina per qualche motivo, viene visualizzata una barra informazioni popup con il messaggio seguente:

**"Sfortunatamente, un processo utilizzato da Visual Studio ha rilevato un errore irreversibile. È consigliabile salvare il lavoro e quindi chiudere e riavviare Visual Studio.**

Se viene visualizzato questo messaggio, salvare il lavoro, quindi chiudere e riavviare Visual Studio.

## <a name="list-of-processes"></a>Elenco dei processi

Di seguito è riportato un elenco di processi out-of-process usati da Visual Studio. L'elenco include i processi che vengono avviati in scenari o flussi di lavoro specifici e quindi, nella maggior parte dei casi, non sono tutti in esecuzione nello stesso momento.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Se uno di questi processi termina in modo imprevisto, alcune funzionalità di Visual Studio smettono di funzionare. Per alcuni processi la perdita di funzionalità può essere irrilevante. Per altri la stabilità di Visual Studio è compromessa e viene visualizzato un messaggio di errore.