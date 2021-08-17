---
title: Errore di accesso remoto del gruppo di lavoro | Microsoft Docs
description: Questo errore può verificarsi quando si esegue il debug da un computer che fa parte di un gruppo di lavoro e si tenta di stabilire la connessione a un computer remoto.
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b88700bf0e0b9a0b07e9806bdb1bb76ae99705801deeb23cc3f24605476b0f36
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391485"
---
# <a name="error-workgroup-remote-logon-failure"></a>Errore: accesso remoto al gruppo di lavoro non riuscito
Il testo del messaggio di errore è il seguente:

 Accesso non riuscito: nome utente sconosciuto o password errata.

 **Causa**

 Questo errore può verificarsi quando si esegue il debug da un computer che fa parte di un gruppo di lavoro e si tenta di stabilire la connessione a un computer remoto. Le cause possibili sono:

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

4. Nella colonna **Criteri** fare doppio clic su **Accesso di rete: modello di condivisione e sicurezza per gli account locali**.

5. Nella finestra di dialogo **Accesso di rete: modello di condivisione e sicurezza per gli account locali** modificare l'impostazione in **Classico: gli utenti locali effettuano l'autenticazione come se stessi**, quindi scegliere il pulsante **Applica**.

     ![Opzioni di sicurezza criteri di sicurezza locali](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Vedi anche
- [Errori di debug remoto e risoluzione dei problemi](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debug remoto](../debugger/remote-debugging.md)
