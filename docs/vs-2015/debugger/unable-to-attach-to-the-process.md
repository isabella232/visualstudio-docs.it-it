---
title: Non è possibile connettersi al processo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 473afbdbbeb510434d45bf28dc02a3ff636d2b9c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968142"
---
# <a name="unable-to-attach-to-the-process"></a>Impossibile connettersi al processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Impossibile connettersi al processo. Accesso negato per il componente del debugger che si trova sul server durante la connessione a questo computer.  
  
 Esistono due scenari comuni in cui viene generato questo errore:  
  
 **Scenario 1:** Nel computer è in esecuzione Windows XP. Nel computer B è in esecuzione Windows Server 2003. Il Registro di sistema del computer B contiene il seguente valore DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 L'utente 1 avvia una sessione Terminal Server (sessione 1) sul computer B e avvia un'applicazione gestita da tale sessione.  
  
 Utente 2, che è amministratore su entrambi i computer, è connesso al computer a Da qui, che potrà tenta di connettersi a un'applicazione in esecuzione nella sessione 1 sul computer B.  
  
 **Scenario 2:** Un utente è connesso a due computer, A e B, nello stesso gruppo di lavoro, usando la stessa password in entrambi i computer. Il debugger sia in esecuzione sul computer A e si tenta di connettersi a un'applicazione gestita in esecuzione nel computer b **accesso alla rete: Modello di condivisione e sicurezza per gli account locali** impostata su **Guest**.  
  
### <a name="to-solve-scenario-1"></a>Per risolvere lo scenario 1  
  
-   Eseguire il debugger e l'applicazione gestita con lo stesso nome account e password.  
  
### <a name="to-solve-scenario-2"></a>Per risolvere lo scenario 2  
  
1.  Fare clic sul pulsante **Start** e scegliere **Pannello di controllo**.  
  
2.  Nel Pannello di controllo fare doppio clic sull'icona **Strumenti di amministrazione**.  
  
3.  Nella finestra Strumenti di amministrazione fare doppio clic su **Criteri di sicurezza locali**.  
  
4.  Nella finestra Criteri di sicurezza locali selezionare **Criteri locali**.  
  
5.  Nel **i criteri** colonna, fare doppio clic su **accesso alla rete: Modello di condivisione e sicurezza per gli account locali**.  
  
6.  Nel **accesso alla rete: Modello di condivisione e sicurezza per gli account locali** finestra di dialogo, modificare l'impostazione di sicurezza locali per **classica**, fare clic su **OK**.  
  
    > [!CAUTION]
    >    L'impostazione del modello di sicurezza su Classico può determinare l'accesso imprevisto a file condivisi e componenti DCOM. In questo caso, un utente remoto può eseguire l'autenticazione con l'account utente locale anziché come Guest. Se il nome utente e la password specificati dall'utente remoto coincidono con quelli dell'account locale, l'utente potrà accedere a qualsiasi cartella o oggetto DCOM condiviso. Se si usa questo modello di sicurezza, assicurarsi che per tutti gli account utente sul computer siano impostate password complesse oppure configurare un'area di rete isolata per i computer coinvolti nelle operazioni di debug in modo da impedire l'accesso non autorizzato.  
  
7.  Chiudere tutte le finestre.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)
