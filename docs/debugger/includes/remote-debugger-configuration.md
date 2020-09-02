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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312100"
---
1. Nel computer remoto individuare e avviare il **debugger remoto** dal menu **Start** . 
   
   Se non si dispone di autorizzazioni amministrative nel computer remoto, fare clic con il pulsante destro del mouse sull'app **remote debugger** e scegliere **Esegui come amministratore**. In caso contrario, è sufficiente avviarlo normalmente.

   Se si prevede di connettersi a un processo in esecuzione come amministratore o se è in esecuzione con un account utente diverso (ad esempio IIS), fare clic con il pulsante destro del mouse sull'app **debugger remoto** e scegliere **Esegui come amministratore**. Per altre informazioni, vedere [eseguire il debugger remoto come amministratore](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. La prima volta che si avvia il debugger remoto (o prima di averlo configurato), viene visualizzata la finestra di dialogo **configurazione debug remoto** .  
  
    ![Configurazione del debugger remoto](../media/remotedebuggerconfwizardpage.png "Configurazione del debugger remoto")  
  
1. Se l'API per servizi Web Windows non è installata, che si verifica solo in Windows Server 2008 R2, selezionare il pulsante **Installa** .  
  
1. Selezionare almeno un tipo di rete in cui si vuole usare Remote Tools. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo Home, scegliere il secondo o il terzo elemento nel modo appropriato.  
  
1. Selezionare **Configura debug remoto** per configurare il firewall e avviare il debugger remoto.  
  
1. Al termine della configurazione, viene visualizzata la finestra **debugger remoto** .
  
    ![Finestra del debugger remoto](../media/remotedebuggerwindow.png "Finestra del debugger remoto")
  
    Il debugger remoto è ora in attesa di una connessione. Usare il nome del server e il numero di porta visualizzato per impostare la configurazione della connessione remota in Visual Studio.  
  
Per arrestare il debugger remoto, selezionare **file**  >  **Esci**. È possibile riavviarlo dal menu **Start** o dalla riga di comando:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
