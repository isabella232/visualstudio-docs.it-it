---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149210"
---
1. Nel computer remoto, trovare e avviare il **Remote Debugger** dalle **avviare** menu. 
   
   Se non hai le autorizzazioni amministrative nel computer remoto, fare doppio clic il **Remote Debugger** app e selezionare **Esegui come amministratore**. In caso contrario, semplicemente avviare normalmente.

   Se si prevede di collegare a un processo di cui è in esecuzione come amministratore o è in esecuzione in un altro utente dell'account (ad esempio IIS), fare doppio clic il **Remote Debugger** app e selezionare **Esegui come amministratore**. Per altre informazioni, vedere [eseguire il debugger remoto come amministratore](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. La prima volta che si avvia il debugger remoto o in precedenza è stato configurato, il **configurazione debug remoto** verrà visualizzata la finestra di dialogo.  
  
    ![Configurazione del Debugger remota](../media/remotedebuggerconfwizardpage.png "configurazione del Debugger remoto")  
  
1. Se l'API di servizi Web di Windows non è installato, situazione che si verifica solo in Windows Server 2008 R2, selezionare la **installare** pulsante.  
  
1. Selezionare il tipo di almeno una rete che si desidera usare remote tools sul. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, scegliere il secondo o il terzo elemento come appropriato.  
  
1. Selezionare **Configura debug remoto** per configurare il firewall e avviare il debugger remoto.  
  
1. Quando la configurazione è completa, il **Remote Debugger** verrà visualizzata la finestra.
  
    ![Finestra del Debugger remoto](../media/remotedebuggerwindow.png "finestra del Debugger remoto")
  
    Il debugger remoto è in attesa di una connessione. Usare il nome del server e porta numero visualizzato per impostare la configurazione della connessione remota in Visual Studio.  
  
Per arrestare il debugger remoto, selezionare **File** > **Exit**. È possibile riavviarlo dal **avviare** dal menu o dalla riga di comando:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
