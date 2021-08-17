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
ms.openlocfilehash: 3994f1bbbf707fad59907d0bd178f61a9629c32f498bb179f8edaa24ff1d2cf5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058312"
---
1. Nel computer remoto individuare e avviare **Remote Debugger** dal menu **Start.** 
   
   Se non si dispone delle autorizzazioni amministrative nel computer remoto, fare clic con il pulsante destro del mouse sull'app **Debugger** remoto e scegliere **Esegui come amministratore**. In caso contrario, è sufficiente avviarlo normalmente.

   Se si prevede di connettersi a un processo in esecuzione come amministratore o in esecuzione con un account utente diverso , ad esempio IIS, fare clic con il pulsante destro del mouse sull'app **Debugger** remoto e scegliere Esegui come **amministratore**. Per altre informazioni, vedere [Eseguire il debugger remoto come amministratore.](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator)
   
1. La prima volta che si avvia il debugger remoto (o prima di configurarlo), viene visualizzata la finestra di dialogo Configurazione **debug** remoto .  
  
    ![Configurazione del debugger remoto](../media/remotedebuggerconfwizardpage.png "Configurazione del debugger remoto")  
  
1. Se l'API Windows Servizi Web non è installata, che si verifica solo Windows Server 2008 R2, selezionare il **pulsante** Installa.  
  
1. Selezionare almeno un tipo di rete in cui usare gli strumenti remoti. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, scegliere il secondo o il terzo elemento in base alle esigenze.  
  
1. Selezionare **Configura debug remoto** per configurare il firewall e avviare il debugger remoto.  
  
1. Al termine della configurazione, viene **visualizzata la finestra Debugger** remoto.
  
    ![Finestra debugger remoto](../media/remotedebuggerwindow.png "Finestra debugger remoto")
  
    Il debugger remoto è ora in attesa di una connessione. Usare il nome del server e il numero di porta visualizzati per impostare la configurazione della connessione remota Visual Studio.  
  
Per arrestare il debugger remoto, selezionare **File** Exit  >  **(Esci da file).** È possibile riavviarlo dal menu **Start** o dalla riga di comando:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
