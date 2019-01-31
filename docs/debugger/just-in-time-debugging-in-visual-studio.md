---
title: Disabilitare il Debugger di Just-In-Time | Microsoft Docs
ms.date: 05/23/18
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edd21719348a69926a32bc23007e37d8bb577de9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983755"
---
# <a name="disable-the-just-in-time-debugger"></a>Disabilitare il debugger JIT 

La finestra di dialogo Debugger JIT può aprire quando si verifica un errore in un'app in esecuzione e l'app non potrà continuare. 

Il Debugger JIT offre la possibilità di avviare Visual Studio per eseguire il debug dell'errore. È necessario disporre [Visual Studio](http://visualstudio.microsoft.com) o un altro debugger selezionato installato per visualizzare informazioni dettagliate sull'errore o provare a eseguirne il debug. 

Se si ha un utente di Visual Studio e si desidera provare a eseguire il debug dell'errore, vedere [eseguire il Debug con il Debugger JIT](../debugger/debug-using-the-just-in-time-debugger.md). Se si non è possibile correggere l'errore o vuole impedire il Debugger JIT di apertura, puoi [Just-In-Time di disabilitare il debug da Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling). 

Se è stato installato Visual Studio, ma non è più eseguire, potrebbe essere necessario [Just-In-Time di disabilitare il debug dal Registro di sistema Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry). 

Se non hai Visual Studio installata, è possibile impedire la disabilitazione di debug di script o il debug sul lato server di debug Just-In-Time. 

- Se si sta tentando di eseguire un'app web, disabilitare il debug degli script:
  
  In Windows **Pannello di controllo** > **rete e Internet** > **Opzioni Internet**selezionare **Disable (debug di script Internet Explorer)** e **Disabilita debugging (altro) degli script**. Le impostazioni e i passaggi esatti dipendono dalla versione di Windows e il browser.
  
  ![Opzioni Internet JIT](../debugger/media/jitinternetoptions.png "opzioni internet JIT")
  
- Se si ospita un'app web ASP.NET in IIS, disabilitare il debug sul lato server:

  1. In Gestione IIS **visualizzazione funzionalità**, sotto il **ASP.NET** fare doppio clic sul **compilazione .NET**, oppure selezionarlo e quindi selezionare **Apri funzionalità**nel **azioni** riquadro. 
  1. Sotto **comportamento** > **Debug**, selezionare **False**. I passaggi sono diversi nelle versioni precedenti di IIS.

Dopo aver disattivato il debug Just-In-Time, l'app potrebbe essere in grado di gestire l'errore ed eseguire normalmente. 

Se l'app contiene ancora un errore non gestito, si può vedere un messaggio di errore o l'app può arrestarsi in modo anomalo o blocco. L'app non viene eseguito in genere fino a quando non viene risolto l'errore. È possibile provare a contattare il proprietario dell'app e chiedere di risolvere il problema.
