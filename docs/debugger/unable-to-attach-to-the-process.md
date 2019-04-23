---
title: Non è possibile connettersi al processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 117d9c57ae5c4a4fbb76a6168fdd6667f3ed6869
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091889"
---
# <a name="unable-to-attach-to-the-process"></a>Impossibile connettersi al processo
Impossibile connettersi al processo. Accesso negato per il componente del debugger che si trova sul server durante la connessione a questo computer.

 Esistono due scenari comuni in cui viene generato questo errore:

 **Scenario 1:** Nel computer è in esecuzione Windows XP. Nel computer B è in esecuzione Windows Server 2003. Il Registro di sistema del computer B contiene il seguente valore DWORD:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 L'utente 1 avvia una sessione Terminal Server (sessione 1) sul computer B e avvia un'applicazione gestita da tale sessione.

 Utente 2, che è amministratore su entrambi i computer, è connesso al computer a Da qui, che potrà tenta di connettersi a un'applicazione in esecuzione nella sessione 1 sul computer B.

 **Scenario 2:** Un utente è connesso a due computer, A e B, nello stesso gruppo di lavoro, usando la stessa password in entrambi i computer. Il debugger sia in esecuzione sul computer A e si tenta di connettersi a un'applicazione gestita in esecuzione nel computer b **accesso alla rete: Modello di condivisione e sicurezza per gli account locali** impostata su **Guest**.

### <a name="to-solve-scenario-1"></a>Per risolvere lo scenario 1

- Eseguire il debugger e l'applicazione gestita con lo stesso nome account e password.

### <a name="to-solve-scenario-2"></a>Per risolvere lo scenario 2

1. Fare clic sul pulsante **Start** e scegliere **Pannello di controllo**.

2. Nel Pannello di controllo fare doppio clic sull'icona **Strumenti di amministrazione**.

3. Nella finestra Strumenti di amministrazione fare doppio clic su **Criteri di sicurezza locali**.

4. Nella finestra Criteri di sicurezza locali selezionare **Criteri locali**.

5. Nel **i criteri** colonna, fare doppio clic su **accesso alla rete: Modello di condivisione e sicurezza per gli account locali**.

6. Nel **accesso alla rete: Modello di condivisione e sicurezza per gli account locali** finestra di dialogo, modificare l'impostazione di sicurezza locali per **classica**, fare clic su **OK**.

    > [!CAUTION]
    >    L'impostazione del modello di sicurezza su Classico può determinare l'accesso imprevisto a file condivisi e componenti DCOM. In questo caso, un utente remoto può eseguire l'autenticazione con l'account utente locale anziché come Guest. Se il nome utente e la password specificati dall'utente remoto coincidono con quelli dell'account locale, l'utente potrà accedere a qualsiasi cartella o oggetto DCOM condiviso. Se si usa questo modello di sicurezza, assicurarsi che per tutti gli account utente sul computer siano impostate password complesse oppure configurare un'area di rete isolata per i computer coinvolti nelle operazioni di debug in modo da impedire l'accesso non autorizzato.

7. Chiudere tutte le finestre.

## <a name="see-also"></a>Vedere anche
- [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)