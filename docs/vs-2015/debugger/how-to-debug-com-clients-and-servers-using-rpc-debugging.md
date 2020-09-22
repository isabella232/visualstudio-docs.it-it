---
title: 'Procedura: eseguire il debug di client e server COM mediante il debug RPC | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fda2a10cd559f940ab87e5cc8c26f5b47dbec194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840303"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Procedura: eseguire il debug di client e server COM mediante il debug RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare il debug RPC (Remote Procedure Call, chiamata a procedura remota) per eseguire il debug delle applicazioni client/server COM. Per utilizzare tale debug, è necessario attivarlo. Quando si chiama il server dal client con il debug RPC attivato, il debugger si connette al server e consente di eseguire il debug del codice. Una volta stabilita la connessione al server, è possibile utilizzare tutte le funzionalità del debugger per i processi del client e del server.  
  
### <a name="to-enable-rpc-debugging"></a>Per attivare il debug RPC  
  
1. Scegliere **Opzioni** dal menu **Strumenti**.  
  
2. Nella finestra di dialogo **Opzioni** fare clic sulla cartella **Debug**.  
  
3. Fare clic sulla pagina **Nativo**.  
  
4. Selezionare la casella di controllo **Debug RPC**.  
  
    > [!NOTE]
    > Per eseguire il debug delle chiamate RPC, è necessario disporre dei privilegi di tipo Administrator o Power User.  
  
    > [!NOTE]
    > L'esecuzione di chiamate RPC a un server remoto che esegue Microsoft Windows Vista funzionerà solo se un debugger nativo è connesso al server remoto. In caso contrario, la chiamata RPC non verrà eseguita senza restituire alcun messaggio di errore oppure verrà completata, ma non funzionerà.  
  
## <a name="see-also"></a>Vedere anche  
 [Server COM e debug del contenitore](../debugger/com-server-and-container-debugging.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)
