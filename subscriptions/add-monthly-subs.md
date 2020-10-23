---
title: Aggiungere nuove sottoscrizioni mensili al portale di amministrazione delle sottoscrizioni | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 09/03/2020
ms.topic: how-to
description: Scopri come acquistare nuove sottoscrizioni mensili di Visual Studio nel portale di amministrazione delle sottoscrizioni
ms.openlocfilehash: f6b835969fff3a8316a2b46c6e15217ebe3e33b1
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467596"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Aggiungere nuove sottoscrizioni mensili di Visual Studio al portale di amministrazione delle sottoscrizioni
Quando si acquistano nuove sottoscrizioni mensili di Visual Studio usando una sottoscrizione di Azure, potrebbe essere necessario aggiungerle al portale di amministrazione delle sottoscrizioni per assegnarle agli utenti.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Ricerca per categorie sa se è necessario aggiungere sottoscrizioni personali?
I passaggi per aggiungere sottoscrizioni mensili dipendono dai tipi di sottoscrizioni già presenti nell'organizzazione e dal fatto che si tratti di un nuovo amministratore.
- Se si è un nuovo amministratore, si verificheranno le sottoscrizioni di Azure per le quali si dispone dei diritti di amministratore di accesso utente quando si accede al portale di amministrazione delle sottoscrizioni la prima volta.  Se vengono rilevate sottoscrizioni mensili, verranno aggiunte automaticamente. 
- Se in precedenza sono state aggiunte o gestite sottoscrizioni mensili, viene verificata la presenza di nuove sottoscrizioni mensili ogni volta che si esegue l'accesso. 
- Se si è già un amministratore per le sottoscrizioni acquistate tramite contratti multilicenza ma non sono state aggiunte o gestite sottoscrizioni mensili in precedenza, sarà necessario aggiungerle usando i passaggi indicati di seguito.

## <a name="how-to-add-monthly-subscriptions"></a>Come aggiungere sottoscrizioni mensili
1. Accedere al portale di amministrazione delle sottoscrizioni all'indirizzo <https://manage.visualstudio.com>
1. Nella scheda **Gestisci sottoscrittori** scegliere l'elenco a discesa **Aggiungi contratto** 
1. Scegliere **nuove sottoscrizioni mensili** nell'elenco a discesa
   > [!div class="mx-imgBorder"]
   > ![Elenco a discesa Aggiungi nuove sottoscrizioni mensili](_img/add-monthly-subs/add-subs-drop-down.png "Scegliere "Aggiungi contratto", quindi "nuove sottoscrizioni mensili.")
1. Il sistema cercherà tutte le sottoscrizioni di Azure per cui si dispone dei diritti di amministratore di accesso utente e importerà tutte le sottoscrizioni di Visual Studio acquistate con le sottoscrizioni di Azure.
1. Se non sono state trovate sottoscrizioni di Azure per cui si hanno diritti di amministratore di accesso utente o se sono state trovate sottoscrizioni di Azure, ma non sono state trovate sottoscrizioni di Visual Studio, verrà visualizzato il messaggio seguente:
   > [!div class="mx-imgBorder"]
   > ![Non sono state trovate nuove sottoscrizioni mensili](_img/add-monthly-subs/no-subs-found.png "Messaggio di errore che indica che non è disponibile alcuna sottoscrizione di Azure o sottoscrizioni di Visual Studio.")
1. Se vengono rilevate nuove sottoscrizioni mensili, verrà visualizzato un messaggio di conferma
   > [!div class="mx-imgBorder"]
   > ![Messaggio di conferma aggiunto alle sottoscrizioni](_img/add-monthly-subs/subs-added-confirmation.png "Un messaggio di conferma visualizzerà le sottoscrizioni aggiunte.")

## <a name="things-to-keep-in-mind"></a>Aspetti da considerare
- L'opzione per aggiungere nuove sottoscrizioni mensili sarà disponibile solo la prima volta che si acquistano.  Dopo aver aggiunto le sottoscrizioni mensili, si verificheranno nuove sottoscrizioni ogni volta che si accede al portale. 
- Quando vengono rilevate nuove sottoscrizioni, si può notare che sono già state assegnate ai sottoscrittori.  Questo perché sono presenti altri amministratori con accesso alla sottoscrizione di Azure e hanno già assegnato le nuove sottoscrizioni di Visual Studio agli utenti.  Ora che sono stati aggiunti anche al portale, è possibile amministrare tali sottoscrizioni. 

## <a name="next-steps"></a>Passaggi successivi
Ora che sono state aggiunte le sottoscrizioni, è possibile assegnarle agli utenti.  Questa operazione può essere eseguita in diversi modi:
- [Assegnazione di sottoscrizioni individualmente](assign-license.md)
- [Assegnare sottoscrizioni a più utenti](assign-license-bulk.md)
- [Assegnare sottoscrizioni specifiche a utenti specifici](assign-guid.md)

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)