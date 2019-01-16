---
title: Eseguire il debug di client e server mediante il debug RPC COM | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42ac7749052fdec3ef9f6cb318af4dc0302e1465
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269263"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Procedura: Eseguire il debug di client e server COM usando il debug RPC
È possibile utilizzare il debug RPC (Remote Procedure Call, chiamata a procedura remota) per eseguire il debug delle applicazioni client/server COM. Per utilizzare tale debug, è necessario attivarlo. Quando si chiama il server dal client con il debug RPC attivato, il debugger si connette al server e consente di eseguire il debug del codice. Una volta stabilita la connessione al server, è possibile utilizzare tutte le funzionalità del debugger per i processi del client e del server.  
  
### <a name="to-enable-rpc-debugging"></a>Per attivare il debug RPC  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** fare clic sulla cartella **Debug**.  
  
3.  Fare clic sulla pagina **Nativo**.  
  
4.  Selezionare la casella di controllo **Debug RPC**.  
  
    > [!NOTE]
    >  Per eseguire il debug delle chiamate RPC, è necessario disporre dei privilegi di tipo Administrator o Power User.  
  
    > [!NOTE]
    >  L'esecuzione di chiamate RPC a un server remoto che esegue Microsoft Windows Vista funzionerà solo se un debugger nativo è connesso al server remoto. In caso contrario, la chiamata RPC non verrà eseguita senza restituire alcun messaggio di errore oppure verrà completata, ma non funzionerà.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei server e dei contenitori COM](../debugger/com-server-and-container-debugging.md)  
 [Debug in Visual Studio](../debugger/index.md)  
 [Presentazione del debugger](../debugger/debugger-feature-tour.md)