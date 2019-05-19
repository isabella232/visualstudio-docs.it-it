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
ms.openlocfilehash: d89dbc0b752c2b8c538ec53769c166b6edbd802f
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65839813"
---
1. Nel computer remoto, trovare e avviare il **Remote Debugger** dalle **avviare** menu. 
   
   Se non hai le autorizzazioni amministrative nel computer remoto, fare doppio clic il **Remote Debugger** app e selezionare **Esegui come amministratore**. In caso contrario, semplicemente avviare normalmente.

   Potrebbero esserci diverse versioni di *msvsmon.exe* nelle *x64*, *x32*, o altre cartelle. Assicurarsi di avviare la versione che necessaria per il debug dell'app. 
   
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
