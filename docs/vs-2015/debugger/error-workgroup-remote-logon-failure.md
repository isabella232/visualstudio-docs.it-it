---
title: 'Errore: Errore di accesso remoto del gruppo di lavoro | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: b13531d3a9dd5249b0c96ddc4e8f736c20696303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723660"
---
# <a name="error-workgroup-remote-logon-failure"></a>Errore: accesso remoto al gruppo di lavoro non riuscito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il testo del messaggio di errore è il seguente:  
  
 Accesso non riuscito: nome utente sconosciuto o password errata.  
  
 **Causa**  
  
 Questo errore può verificarsi quando si esegue il debug da un computer che fa parte di un gruppo di lavoro e si tenta di stabilire la connessione a un computer remoto. Fra le cause possibili vi sono le seguenti:  
  
-   Nel computer remoto non esiste un account con il nome e la password specificati.  
  
-   Se il computer di Visual Studio sia nel computer remoto sono in gruppi di lavoro, questo errore può verificarsi a causa dell'impostazione predefinita **criteri di sicurezza locali** impostazione nel computer remoto. L'impostazione predefinita per il **criteri di sicurezza locali** impostazione **solo Guest: gli utenti locali effettuano l'autenticazione come Guest**. Per eseguire il debug con questa configurazione, è necessario modificare l'impostazione del computer remoto in **classico: gli utenti locali effettuano l'autenticazione come se stessi**.  
  
> [!NOTE]
>  Per effettuare le attività elencate di seguito è necessario disporre di diritti amministrativi.  
  
### <a name="to-open-the-local-security-policy-window"></a>Per aprire la finestra Criteri di sicurezza locali  
  
1.  Avviare il **secpol. msc** snap-in Microsoft Management Console. Digitare secpol.msc nella funzionalità di ricerca di Windows, nella casella Esegui di Windows o a un prompt dei comandi.  
  
### <a name="to-add-user-rights-assignments"></a>Per aggiungere assegnazioni di diritti utente  
  
1.  Aprire la  
  
2.  Aprire il **criteri di sicurezza locali** finestra.  
  
3.  Espandere la **criteri locali** cartella.  
  
4.  Fare clic su **Assegnazione diritti utente**.  
  
5.  Nel **criterio** colonna, fare doppio clic su **il Debug dei programmi** per visualizzare le assegnazioni di criteri di gruppo locale corrente nel **impostazioni di criteri di sicurezza locali** nella finestra di dialogo.  
  
     ![Diritti utente criteri di sicurezza locali](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Per aggiungere nuovi utenti, scegliere il **Aggiungi utente o gruppo** pulsante.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Per modificare il modello di condivisione e sicurezza  
  
1.  Aprire il **criteri di sicurezza locali** finestra.  
  
2.  Espandere la **criteri locali** cartella.  
  
3.  Fare clic su **opzioni di sicurezza**.  
  
4.  Nel **criterio** colonna, fare doppio clic su **l'accesso alla rete: modello di condivisione e sicurezza per gli account locali**.  
  
5.  Nel **l'accesso alla rete: modello di condivisione e sicurezza per gli account locali** finestra di dialogo, modificare il valore da **classico: gli utenti locali effettuano l'autenticazione come se stessi** e fare clic sui **applica**pulsante.  
  
     ![Le opzioni di sicurezza dei criteri di sicurezza locali](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



