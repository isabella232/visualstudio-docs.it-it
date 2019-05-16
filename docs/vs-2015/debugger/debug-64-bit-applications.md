---
title: Il debug di applicazioni a 64 bit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f67acff26d346b915f6b457fc0887f1d5f2ec3b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695908"
---
# <a name="debug-64-bit-applications"></a>Eseguire il debug di applicazioni a 64 bit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Debug 64-Bit Applications](https://docs.microsoft.com/visualstudio/debugger/debug-64-bit-applications) .  
  
È possibile eseguire il debug di un'applicazione a 64 bit in esecuzione nel computer locale o in un computer remoto.  
  
 Per eseguire il debug di un'applicazione a 64 bit in esecuzione in un computer remoto, vedere [Remote Debugging](../debugger/remote-debugging.md).  
  
 Per eseguire il debug delle applicazioni a 64 bit in locale, Visual Studio usa un processo di lavoro a 64 bit (msvsmon.exe) per eseguire le operazioni a basso livello che non possono essere eseguite all'interno del processo di Visual Studio a 32 bit.  
  
 Il debug in modalità mista non è supportato per i processi a 64 bit che usano .NET Framework 3.5 o versioni precedenti.  
  
## <a name="debug-a-64-bit-application"></a>Debug di un'applicazione a 64 bit  
 Per provare a eseguire il debug di applicazioni a 64 bit:  
  
1. Creare una soluzione di Visual Studio, ad esempio un'applicazione console C#.  
  
2. Impostare la configurazione su 64 bit tramite Gestione configurazione. Per altre informazioni, vedere [Procedura: Configurare progetti per le piattaforme di destinazione](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3. A questo punto verrà avviata la versione a 64 bit del debugger remoto (msvsmon.exe). Questa viene eseguita finché la soluzione con la configurazione a 64 bit è aperta.  
  
4. Avviare il debug. L'esperienza dovrebbe corrispondere a quella di una configurazione a 32 bit. Se si verificano errori, vedere la sezione relativa alla risoluzione dei problemi di seguito.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Risoluzione dei problemi di debug a 64 bit  
 Potrebbe essere visualizzato un errore: "Un'operazione di debug a 64 bit richiede più tempo del previsto." In questo caso, Visual Studio ha inviato una richiesta alla versione a 64 bit di msvsmon.exe ed è stato necessario molto tempo per la restituzione del risultato di tale richiesta.  
  
 Questo errore può avere due cause principali:  
  
- Nel computer è installato software di sicurezza di rete che ha reso non affidabile lo stack di rete e ha eliminato alcuni pacchetti trasmessi tramite localhost. Provare a disabilitare tutto il software di sicurezza di rete e determinare se questo consente di risolvere il problema. In questo caso, segnalare al fornitore del software di sicurezza di rete che il software interferisce con traffico di localhost.  
  
- Si è verificato un blocco o un problema di prestazioni di Visual Studio. Se il problema si verifica regolarmente, è possibile raccogliere dump di Visual Studio (devenv.exe) e del processo di lavoro (msvsmon.exe) e inviarli a Microsoft. 
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni a 64 bit](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Configurazione di programmi per processori a 64 bit](https://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Supporto a 64 bit per l'IDE di Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Uso di file dump](../debugger/using-dump-files.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
