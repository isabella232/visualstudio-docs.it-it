---
title: Le assegnazioni di porta del Debugger remoto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c1e70ec3ba50e5be1ed532bb4a88cbdd500af09c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965372"
---
# <a name="remote-debugger-port-assignments"></a>Assegnazioni delle porte del debugger remoto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Remote Debugger può essere eseguito come applicazione o come servizio in background. Quando viene eseguito come applicazione, usa una porta assegnata per impostazione predefinita, come indicato di seguito:  
  
- Visual Studio 2015: 4020  
  
- Visual Studio 2013: 4018  
  
- Visual Studio 2012: 4016  
  
  In altre parole, il numero della porta assegnata al debugger remoto viene incrementato di 2 per ogni versione. È possibile impostare un numero di porta diverso. In una sezione successiva verrà illustrato come impostare i numeri di porta.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Porta del debugger remoto nei sistemi operativi a 32 bit  
 TCP 4020 (in Visual Studio 2015) è la porta principale ed è necessaria per tutti gli scenari. Può essere configurata dalla riga di comando o nella finestra del debugger remoto.  
  
 Nella finestra del debugger remoto, fare clic su **Strumenti / opzioni**, e impostare il numero di porta TCP/IP.  
  
 Nella riga di comando avviare il debugger remoto con l'opzione **/port**: **msvsmon /port \<numero porta>**.  
  
 Tutte le opzioni della riga di comando del debugger remoto sono reperibili nella Guida al debug remoto (premere **F1** o fare clic su **Guida / Utilizzo** nella finestra del debugger remoto).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Porta del debugger remoto nei sistemi operativi a 64 bit  
 Quando viene avviata, la versione a 64 bit del debugger remoto usa la porta 4020 per impostazione predefinita.  Se si esegue il debug di un processo a 32 bit, la versione a 64 bit del debugger remoto avvia una versione a 32 bit del debugger remoto sulla porta 4021. Se si esegue il debugger remoto a 32 bit, viene usata la porta 4020 e non la porta 4021.  
  
 Questa porta è configurabile dalla riga di comando: **Msvsmon /wow64port \<numero porta >**.  
  
## <a name="the-discovery-port"></a>Porta di individuazione  
 La porta UDP 3702 viene usata per individuare le istanze in esecuzione del debugger remoto sulla rete, ad esempio la finestra di dialogo **Trova** nella finestra di dialogo **Connetti a processo** . Viene usata solo per l'individuazione di un computer che esegue il debugger remoto, pertanto è facoltativa se si ha altro un modo per conoscere il nome del computer o l'indirizzo IP del computer di destinazione. Si tratta di una porta standard per l'individuazione, quindi non è possibile configurare il numero di porta.  
  
 Se non si desidera abilitare l'individuazione, è possibile avviare msvsmon dalla riga di comando con l'individuazione disabilitata:  **Msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Porte del debugger remoto in Azure  
 Il debugger remoto in Azure usa le porte indicate di seguito. Le porte del servizio cloud sono mappate alle porte nelle singole macchine virtuali. Tutte le porte sono TCP.  
  
||||  
|-|-|-|  
|**Connessione**|**Porta sul servizio cloud**|**Porta sulla macchina virtuale**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Vedere anche  
 [Remote Debugging](../debugger/remote-debugging.md)
