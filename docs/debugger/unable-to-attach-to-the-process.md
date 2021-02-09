---
title: Non è possibile connettersi al processo | Microsoft Docs
description: Informazioni sul significato di "Impossibile connettersi al processo", dei due scenari che lo provocano e delle soluzioni.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f83a4f262e394222d420c2fec187e67ddfbfaf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870415"
---
# <a name="unable-to-attach-to-the-process"></a>Impossibile connettersi al processo
Impossibile connettersi al processo. Accesso negato per il componente del debugger che si trova sul server durante la connessione a questo computer.

 Esistono due scenari comuni in cui viene generato questo errore:

 **Scenario 1:** nel computer A è in esecuzione Windows XP. Nel computer B è in esecuzione Windows Server 2003. Il Registro di sistema del computer B contiene il seguente valore DWORD:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 L'utente 1 avvia una sessione Terminal Server (sessione 1) sul computer B e avvia un'applicazione gestita da tale sessione.

 L'utente 2, che è l'amministratore di entrambi i computer, viene registrato sul computer A. Da qui, tenta di connettersi a un'applicazione in esecuzione nella sessione 1 nel computer B.

 **Scenario 2:** un utente è connesso a due computer, A e B, appartenenti allo stesso gruppo di lavoro e usa la stessa password per entrambi i computer. Il debugger è in esecuzione nel computer A e tenta di connettersi a un'applicazione gestita in esecuzione nel computer B. il computer A dispone di **accesso alla rete: modello di condivisione e sicurezza per gli account locali** impostati su **Guest**.

### <a name="to-solve-scenario-1"></a>Per risolvere lo scenario 1

- Eseguire il debugger e l'applicazione gestita con lo stesso nome account e password.

### <a name="to-solve-scenario-2"></a>Per risolvere lo scenario 2

1. Fare clic sul pulsante **Start** e scegliere **Pannello di controllo**.

2. Nel Pannello di controllo fare doppio clic sull'icona **Strumenti di amministrazione**.

3. Nella finestra strumenti di amministrazione fare doppio clic su **criteri di sicurezza locali**.

4. Nella finestra Criteri di sicurezza locali selezionare **Criteri locali**.

5. Nella colonna **Criteri** fare doppio clic su **Accesso di rete: modello di condivisione e sicurezza per gli account locali**.

6. Nella finestra di dialogo **Accesso di rete: modello di condivisione e sicurezza per gli account locali** impostare la sicurezza locale su **Classico**, quindi scegliere **OK**.

    > [!CAUTION]
    >   L'impostazione del modello di sicurezza su Classico può determinare l'accesso imprevisto a file condivisi e componenti DCOM. In questo caso, un utente remoto può eseguire l'autenticazione con l'account utente locale anziché come Guest. Se un utente remoto corrisponde al nome utente e alla password, l'utente potrà accedere a qualsiasi cartella o oggetto DCOM che è stato condiviso. Se si usa questo modello di sicurezza, assicurarsi che tutti gli account utente nel computer dispongano di password complesse oppure configurare un'isola di rete isolata per il debug e i computer sottoposti a debug per impedire l'accesso non autorizzato.

7. Chiudere tutte le finestre.

## <a name="see-also"></a>Vedi anche
- [Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)