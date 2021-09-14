---
title: Aggiungere nuove sottoscrizioni mensili al portale di amministrazione delle sottoscrizioni | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 03/19/2021
ms.topic: how-to
description: Informazioni su come acquistare sottoscrizioni mensili Visual Studio al portale di amministrazione delle sottoscrizioni
ms.openlocfilehash: 931f297a650926e4da5c13271a58091c9f00ddd3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709984"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Aggiungere nuove sottoscrizioni Visual Studio al portale di amministrazione delle sottoscrizioni
Quando si acquistano nuove sottoscrizioni Visual Studio con una sottoscrizione di Azure, potrebbe essere necessario aggiungerle al portale di amministrazione delle sottoscrizioni per assegnarle agli utenti.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Ricerca per categorie se è necessario aggiungere le sottoscrizioni?
La procedura per aggiungere sottoscrizioni mensili dipende dai tipi di sottoscrizioni già presenti nell'organizzazione e dal fatto che si sia un nuovo amministratore.
- Se si è un nuovo amministratore, verranno verificate le sottoscrizioni di Azure per le quali si hanno diritti di amministratore accesso utente quando si accede al portale di amministrazione delle sottoscrizioni la prima volta.  Se vengono trovate sottoscrizioni mensili, verranno aggiunti automaticamente. 
- Se in precedenza sono state aggiunte o amministrate sottoscrizioni mensili, viene verificata la presenza di nuove sottoscrizioni mensili ogni volta che si accede. 
- Se si è già un amministratore per le sottoscrizioni acquisite tramite contratti multilicenza ma non sono state aggiunte o gestite in precedenza sottoscrizioni mensili, è necessario aggiungerle usando la procedura descritta di seguito.

## <a name="how-to-add-monthly-subscriptions"></a>Come aggiungere sottoscrizioni mensili
1. Accedere al portale di amministrazione delle sottoscrizioni all'indirizzo <https://manage.visualstudio.com>
1. Nella scheda **Gestisci sottoscrittori** scegliere l'elenco a discesa **Aggiungi** contratto 
1. Scegliere **Nuove sottoscrizioni mensili** nell'elenco a discesa
   > [!div class="mx-imgBorder"]
   > ![Elenco a discesa Aggiungi nuove sottoscrizioni mensili](_img/add-monthly-subs/add-subs-drop-down.png "Scegliere &quot;Aggiungi contratto&quot;, quindi &quot;Nuove sottoscrizioni mensili&quot;.")
1. Il sistema cerca tutte le sottoscrizioni di Azure per cui si dispone dei diritti di amministratore accesso utente e importa tutte le sottoscrizioni Visual Studio acquistate con tali sottoscrizioni di Azure.
1. Se non viene trovata alcuna sottoscrizione di Azure per cui si dispone dei diritti di amministratore accesso utente o se vengono trovate sottoscrizioni di Azure idonee ma non vengono trovate sottoscrizioni Visual Studio, verrà visualizzato il messaggio seguente:
   > [!div class="mx-imgBorder"]
   > ![Non sono stati trovati nuovi abbonamenti mensili](_img/add-monthly-subs/no-subs-found.png "Messaggio di errore che indica che non sono disponibili sottoscrizioni di Azure o Visual Studio disponibili.")
1. Se vengono trovate nuove sottoscrizioni mensili, verrà visualizzato un messaggio di conferma
   > [!div class="mx-imgBorder"]
   > ![Messaggio di conferma delle sottoscrizioni aggiunte](_img/add-monthly-subs/subs-added-confirmation.png "Verrà visualizzato un messaggio di conferma per visualizzare le sottoscrizioni aggiunte.")

## <a name="things-to-keep-in-mind"></a>Aspetti da considerare
- L'opzione per aggiungere nuove sottoscrizioni mensili sarà disponibile solo la prima volta che vengono acquistate.  Dopo aver aggiunto le sottoscrizioni mensili, verrà verificata la presenza di nuove sottoscrizioni ogni volta che si accede al portale. 
- Quando vengono trovate nuove sottoscrizioni, è possibile che siano già assegnate ai sottoscrittori.  Questo perché sono presenti altri amministratori con accesso alla sottoscrizione di Azure e hanno già assegnato le nuove sottoscrizioni Visual Studio agli utenti.  Ora che sono state aggiunte anche al portale, è possibile amministrare tali sottoscrizioni. 

## <a name="support-resources"></a>Risorse di supporto
- Per assistenza per l'amministrazione di Sottoscrizioni di Visual Studio, contattare il [supporto Visual Studio sottoscrizioni](https://aka.ms/vsadminhelp).

## <a name="next-steps"></a>Passaggi successivi
Dopo aver aggiunto le sottoscrizioni, è possibile assegnarle agli utenti.  È possibile eseguire questa operazione in diversi modi:
- [Assegnare le sottoscrizioni singolarmente](assign-license.md)
- [Assegnare sottoscrizioni a più utenti](assign-license-bulk.md)
- [Assegnare sottoscrizioni specifiche a utenti specifici](assign-guid.md)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)