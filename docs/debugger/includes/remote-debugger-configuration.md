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
ms.openlocfilehash: b6e312f7e1913a8b4533c0127b966dc3ac0d981d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809257"
---
È necessario disporre delle autorizzazioni amministrative nel computer remoto.  
  
1.  Trovare l'applicazione del debugger remoto. (Individuare msvsmon.exe nella posizione in cui è stato installato, o aprire il menu Start e cercare **Remote Debugger**.)
  
     Se si esegue il debugger remoto in un server remoto, è possibile fare doppio clic il Debugger remoto di app e scegliere **Esegui come amministratore**. Se non si vengono eseguite in un server remoto, semplicemente avviare normalmente.
  
3.  Quando si avvia remote tools per la prima volta (o prima che sia stato configurato), il **configurazione debug remoto** verrà visualizzata la finestra di dialogo.  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Se l'API del servizio Windows non è installato (che si verifica solo in Windows Server 2008 R2), scegliere il **installare** pulsante.  
  
5.  Selezionare i tipi di reti su cui usare Remote Tools. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento a seconda delle esigenze.  
  
6.  Scegli **Configura debug remoto** per configurare il firewall e avviare lo strumento.  
  
7.  Al termine della configurazione viene visualizzata la finestra del debugger remoto.
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     Il debugger remoto è in attesa di una connessione. Prendere nota del nome del server e il numero che viene visualizzato, porta, poiché questo deve corrispondere alla configurazione in un secondo momento usare in Visual Studio.  
  
 Al termine delle operazioni di debug ed è necessario arrestare il debugger remoto, fare clic su **File > Esci** nella finestra. È possibile riavviarlo dal **avviare** menu o dalla riga di comando:  
  
 **\<Directory di installazione di Remote debugger >\\< x86, x64, ARM, ARM64 o Appx > \msvsmon.exe**.  
