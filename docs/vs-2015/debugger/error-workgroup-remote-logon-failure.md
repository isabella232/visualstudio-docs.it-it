---
title: 'Errore: accesso remoto al gruppo di lavoro non riuscito | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 09f018982b81535ae23eafe7158aa88c0b6b08a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839575"
---
# <a name="error-workgroup-remote-logon-failure"></a>Errore: accesso remoto al gruppo di lavoro non riuscito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
1. Aprire la  
  
2. Aprire la finestra **Criteri di sicurezza locali**.  
  
3. Espandere la cartella **Criteri locali**.  
  
4. Scegliere **Assegnazione diritti utente**.  
  
5. Nella colonna **Criteri** fare doppio clic su **Debug di programmi** per visualizzare le assegnazioni dei criteri di gruppo locali correnti nella finestra di dialogo relativa all'**impostazione di criteri di sicurezza locali**.  
  
     ![Diritti utente criteri di sicurezza locali](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6. Per aggiungere nuovi utenti, fare clic sul pulsante **Aggiungi utente o gruppo**.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Per modificare il modello di condivisione e sicurezza  
  
1. Aprire la finestra **Criteri di sicurezza locali**.  
  
2. Espandere la cartella **Criteri locali**.  
  
3. Fare clic su **Opzioni di sicurezza**.  
  
4. Nella colonna **Criteri** fare doppio clic su **Accesso di rete: modello di condivisione e sicurezza per gli account locali**.  
  
5. Nella finestra di dialogo **Accesso di rete: modello di condivisione e sicurezza per gli account locali** modificare l'impostazione in **Classico: gli utenti locali effettuano l'autenticazione come se stessi**, quindi scegliere il pulsante **Applica**.  
  
     ![Opzioni di sicurezza criteri di sicurezza locali](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Vedere anche  
 [Errori e risoluzione dei problemi di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)
