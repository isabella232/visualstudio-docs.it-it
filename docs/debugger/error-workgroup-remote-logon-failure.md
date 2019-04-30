---
title: "Errore: Errore durante l'accesso remoto del gruppo di lavoro | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d9142e92367dd10653bb8fdaaf86c34f3f17b84
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399239"
---
# <a name="error-workgroup-remote-logon-failure"></a>Errore: Accesso remoto al gruppo di lavoro non riuscito
Il testo del messaggio di errore è il seguente:

 Accesso non riuscito: nome utente sconosciuto o password errata.

 **Causa**

 Questo errore può verificarsi quando si esegue il debug da un computer che fa parte di un gruppo di lavoro e si tenta di stabilire la connessione a un computer remoto. Fra le cause possibili vi sono le seguenti:

- Nel computer remoto non esiste un account con il nome e la password specificati.

- Se il computer di Visual Studio e il computer remoto fanno entrambi parte di gruppi di lavoro, questo errore può essere causato dall'impostazione predefinita di **Criteri di sicurezza locali** del computer remoto. L'impostazione predefinita di **Criteri di sicurezza locali** è **Solo Guest: gli utenti locali effettuano l'autenticazione come Guest**. Per eseguire il debug con questa configurazione, è necessario modificare l'impostazione del computer remoto in **Classico: gli utenti locali effettuano l'autenticazione di se stessi**.

> [!NOTE]
> Per effettuare le attività elencate di seguito è necessario disporre di diritti amministrativi.

### <a name="to-open-the-local-security-policy-window"></a>Per aprire la finestra Criteri di sicurezza locali

1. Avviare lo snap-in **secpol.msc** di Microsoft Management Console. Digitare secpol.msc nella funzionalità di ricerca di Windows, nella casella Esegui di Windows o a un prompt dei comandi.

### <a name="to-add-user-rights-assignments"></a>Per aggiungere assegnazioni di diritti utente

1. Aprire la finestra **Criteri di sicurezza locali**.

2. Espandere la cartella **Criteri locali**.

3. Scegliere **Assegnazione diritti utente**.

4. Nella colonna **Criteri** fare doppio clic su **Debug di programmi** per visualizzare le assegnazioni dei criteri di gruppo locali correnti nella finestra di dialogo relativa all'**impostazione di criteri di sicurezza locali**.

     ![Diritti utente criteri di sicurezza locali](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5. Per aggiungere nuovi utenti, fare clic sul pulsante **Aggiungi utente o gruppo**.

### <a name="to-change-the-sharing-and-security-model"></a>Per modificare il modello di condivisione e sicurezza

1. Aprire la finestra **Criteri di sicurezza locali**.

2. Espandere la cartella **Criteri locali**.

3. Fare clic su **Opzioni di sicurezza**.

4. Nel **criterio** colonna, fare doppio clic su **accesso alla rete: Modello di condivisione e sicurezza per gli account locali**.

5. Nel **accesso alla rete: Modello di condivisione e sicurezza per gli account locali** finestra di dialogo, modificare il valore per **classico: gli utenti locali autenticarsi con il proprio** e fare clic sui **applica** pulsante.

     ![Le opzioni di sicurezza dei criteri di sicurezza locali](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Vedere anche
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)