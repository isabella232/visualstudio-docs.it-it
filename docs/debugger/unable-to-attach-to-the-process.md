---
title: Impossibile connettersi al processo | Microsoft Docs
description: Informazioni sul significato di "Impossibile connettersi al processo", i due scenari che lo causano e le soluzioni.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 26698cc8655c269cdbac69d4c54aac2fc3c3193a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112290"
---
# <a name="unable-to-attach-to-the-process"></a>Impossibile connettersi al processo
Impossibile connettersi al processo. Accesso negato per il componente del debugger che si trova sul server durante la connessione a questo computer.

 Esistono due scenari comuni in cui viene generato questo errore:

 **Scenario 1:** nel computer A è in esecuzione Windows XP. Nel computer B è in esecuzione Windows Server 2003. Il Registro di sistema del computer B contiene il seguente valore DWORD:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 L'utente 1 avvia una sessione Terminal Server (sessione 1) sul computer B e avvia un'applicazione gestita da tale sessione.

 L'utente 2, amministratore di entrambi i computer, è connesso al computer A. Da qui, tenta di connettersi a un'applicazione in esecuzione nella sessione 1 nel computer B.

 **Scenario 2:** un utente è connesso a due computer, A e B, appartenenti allo stesso gruppo di lavoro e usa la stessa password per entrambi i computer. Il debugger è in esecuzione nel computer A e tenta di connettersi a un'applicazione gestita in esecuzione nel computer B. Il computer A ha accesso alla **rete:** Modello di condivisione e sicurezza per gli account locali impostato su **Guest.**

### <a name="to-solve-scenario-1"></a>Per risolvere lo scenario 1

- Eseguire il debugger e l'applicazione gestita con lo stesso nome account e password.

### <a name="to-solve-scenario-2"></a>Per risolvere lo scenario 2

1. Fare clic sul pulsante **Start** e scegliere **Pannello di controllo**.

2. Nel Pannello di controllo fare doppio clic sull'icona **Strumenti di amministrazione**.

3. Nella finestra Strumenti di amministrazione fare doppio clic su **Criteri di sicurezza locali**.

4. Nella finestra Criteri di sicurezza locali selezionare **Criteri locali**.

5. Nella colonna **Criteri** fare doppio clic su **Accesso di rete: modello di condivisione e sicurezza per gli account locali**.

6. Nella finestra di dialogo **Accesso di rete: modello di condivisione e sicurezza per gli account locali** impostare la sicurezza locale su **Classico**, quindi scegliere **OK**.

    > [!CAUTION]
    >   L'impostazione del modello di sicurezza su Classico può determinare l'accesso imprevisto a file condivisi e componenti DCOM. In questo caso, un utente remoto può eseguire l'autenticazione con l'account utente locale anziché come Guest. Se un utente remoto corrisponde al nome utente e alla password, potrà accedere a qualsiasi cartella o oggetto DCOM condiviso. Se si usa questo modello di sicurezza, assicurarsi che tutti gli account utente nel computer abbiano password complesse o configurare un'isola di rete isolata per i computer di debug e di debug per impedire l'accesso non autorizzato.

7. Chiudere tutte le finestre.

## <a name="see-also"></a>Vedi anche
- [Preparazione e Impostazioni debugger](../debugger/debugger-settings-and-preparation.md)