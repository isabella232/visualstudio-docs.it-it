---
title: Eseguire il debug di applicazioni a 64 bit | Microsoft Docs
description: Informazioni su come eseguire il debug di un'applicazione a 64 bit con Visual Studio. Sono disponibili suggerimenti per la risoluzione dei ritardi imprevisti del debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dc3a841d97b3479eb30d26d66608827e1a771d20
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630815"
---
# <a name="debug-64-bit-applications"></a>Eseguire il debug di applicazioni a 64 bit
È possibile eseguire il debug di un'applicazione a 64 bit in esecuzione nel computer locale o in un computer remoto.

 Per eseguire il debug di un'applicazione a 64 bit in esecuzione in un computer remoto, vedere [Remote Debugging](../debugger/remote-debugging.md).

 Per eseguire il debug delle applicazioni a 64 bit in locale, Visual Studio usa un processo di lavoro a 64 bit (msvsmon.exe) per eseguire le operazioni a basso livello che non possono essere eseguite all'interno del processo di Visual Studio a 32 bit.

 Il debug in modalità mista non è supportato per i processi a 64 bit che usano .NET Framework 3.5 o versioni precedenti.

## <a name="debug-a-64-bit-application"></a>Debug di un'applicazione a 64 bit
 Per provare a eseguire il debug di applicazioni a 64 bit:

1. Creare una soluzione di Visual Studio, ad esempio un'applicazione console C#.

2. Impostare la configurazione su 64 bit tramite Gestione configurazione. Per altre informazioni, vedere [How to: Configure Projects to Target Platforms](../ide/how-to-configure-projects-to-target-platforms.md).

3. A questo punto verrà avviata la versione a 64 bit del debugger remoto (msvsmon.exe). Questa viene eseguita finché la soluzione con la configurazione a 64 bit è aperta.

4. Avviare il debug. L'esperienza dovrebbe corrispondere a quella di una configurazione a 32 bit. Se si verificano errori, vedere la sezione relativa alla risoluzione dei problemi di seguito.

## <a name="troubleshooting-64-bit-debugging"></a>Risoluzione dei problemi di debug a 64 bit
 Potrebbe essere visualizzato un errore: "Un'operazione di debug a 64 bit richiede più tempo del previsto". In questo caso, Visual Studio ha inviato una richiesta alla versione a 64 bit di msvsmon.exe ed è stato necessario molto tempo per la restituzione del risultato di tale richiesta.

 Questo errore può avere due cause principali:

- Nel computer è installato software di sicurezza di rete che ha reso non affidabile lo stack di rete e ha eliminato alcuni pacchetti trasmessi tramite localhost. Provare a disabilitare tutto il software di sicurezza di rete e determinare se questo consente di risolvere il problema. In questo caso, segnalare al fornitore del software di sicurezza di rete che il software interferisce con traffico di localhost.

- Si verifica un problema a causa del quale Visual Studio non risponde o un altro problema di prestazioni. Se il problema si verifica regolarmente, è possibile raccogliere dump di Visual Studio (devenv.exe) e del processo di lavoro (msvsmon.exe) e inviarli a Microsoft. Per informazioni sulla segnalazione di un problema, vedere [How to Report a Problem with Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Applicazioni a 64 bit](/dotnet/framework/64-bit-apps)
- [Configurazione di programmi per processori a 64 bit](/cpp/build/configuring-programs-for-64-bit-visual-cpp)
- [Visual Studio Supporto IDE a 64 bit](../ide/visual-studio-ide-64-bit-support.md)
- [Uso di file dump](../debugger/using-dump-files.md)
- [Debug remoto](../debugger/remote-debugging.md)