---
title: Errore irreversibile del processo di Visual Studio
ms.date: 02/23/2017
ms.topic: troubleshooting
helpviewer_keywords:
- editor
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 1db7f2729ded01eedda6fff6d18ca1b2ee3607b6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# Errore irreversibile del processo di Visual Studio

Visual Studio 2017 usa diversi processi out-of-process per svolgere le attività necessarie in background, ad esempio testing unità in tempo reale, analizzatori di codice e altro ancora. Questi processi vengono eseguiti out-of-process per offrire vantaggi in termini di prestazioni di Visual Studio, consentendo ad esempio a Visual Studio per rispondere più rapidamente durante l'esecuzione di processi a lunga durata e con uso intensivo di risorse. E poiché Visual Studio è un processo a 32 bit, l'esecuzione di processi out-of-process rende disponibile uno spazio di memoria più grande dove svolgere le attività con uso intensivo della memoria.

Se uno dei processi richiesti termina per qualche motivo, viene visualizzata una barra informazioni popup in cui un messaggio indica che

in un processo usato da Visual Studio si è verificato un errore irreversibile e che è consigliabile salvare il lavoro e quindi chiudere e riavviare Visual Studio.

Se viene visualizzato questo messaggio, salvare immediatamente il lavoro, quindi chiudere e riavviare Visual Studio. Se non si esegue questa operazione, Visual Studio può arrestarsi in modo anomalo in qualsiasi momento.

## Elenco dei processi

Di seguito è riportato un elenco di processi out-of-process usati da Visual Studio che devono essere in esecuzione perché Visual Studio funzioni correttamente.

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