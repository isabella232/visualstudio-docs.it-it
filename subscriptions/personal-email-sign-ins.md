---
title: Messaggi di posta elettronica personali per Visual Studio sottoscrizioni in VLSC
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 03/21/2021
ms.topic: conceptual
description: Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori?
ms.openlocfilehash: fe1f9a293109c168c7cfcadda2ca98db3fa9a942
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128375702"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Visual Studio sottoscrizioni: perché vengono visualizzati gli account personali per i sottoscrittori?
Dopo che le aziende hanno eseguito la migrazione dal Volume Licensing Service Center (VLSC) al nuovo portale di amministrazione delle sottoscrizioni di [Visual Studio,](https://manage.visualstudio.com)gli amministratori si sono trovati disappresi nel vedere che l'indirizzo di posta elettronica di accesso per alcuni sottoscrittori mostra un indirizzo di posta elettronica personale, ad esempio Hotmail o Outlook.  

## <a name="cause"></a>Causa
Questa situazione si verifica a causa dei processi di accesso associati all'esperienza legacy degli abbonati a MSDN. La migrazione degli utenti da Volume License Service Center (VLSC) al portale di amministrazione delle sottoscrizioni di Visual Studio è stata completata senza modifiche. Gli amministratori potrebbero non essere a conoscenza del fatto che gli utenti usavano account personali per accedere ai vantaggi della sottoscrizione. Prima delle migrazioni dei sottoscrittori di Visual Studio, completate nel 2016, erano necessarie due azioni per usare correttamente una sottoscrizione di Visual Studio:
1. L'amministratore ha "assegnato" la sottoscrizione a un singolo sottoscrittore, usando il proprio indirizzo di posta elettronica di lavoro o dell'istituto di istruzione.
2. Il sottoscrittore "attivava" la sottoscrizione.

Durante il processo di attivazione del sottoscrittore, veniva richiesto un account Microsoft per eseguire l'accesso. Se il sottoscrittore non tentava di convertire l'account aziendale o dell'istituto di istruzione (ad esempio tasha@contoso.com) in un account Microsoft, poteva creare un nuovo account Microsoft o sfruttarne uno esistente. A causa di tutto ciò, l'indirizzo di posta elettronica di accesso può risultare diverso dall'indirizzo di posta elettronica di assegnazione.

> [!NOTE]
> L'esperienza moderna per i sottoscrittori in supporta sia i tipi di identità aziendale/dell'istituto di istruzione che i tipi di [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) identità dell'account Microsoft.

## <a name="solution"></a>Soluzione
Per risolvere il problema, è sufficiente selezionare il pulsante Connessione Emails (Messaggi di posta elettronica di **Connessione)** e il sistema tenterà di associare gli account con account del servizio gestiti agli utenti esistenti nel Azure Active Directory (Azure AD) dell'organizzazione in base alla corrispondenza del nome e del cognome. Se si verifica un errore, è possibile rimuovere qualsiasi corrispondenza facendo clic sulla **X** a destra della corrispondenza.  

Guardare questo video o continuare a leggere per informazioni su come risolvere il problema. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![Connessione Pulsante Messaggi di posta elettronica](_img/connect-emails/connect-emails-button.png "Fare clic Connessione di posta elettronica per associare gli utenti con gli account Microsoft all'Azure Active Directory")

È anche possibile usare la **directory di** ricerca per correggere gli errori o inserire le informazioni mancanti dal Azure AD. Se tutte le corrispondenze sono corrette, è possibile scegliere il pulsante Identità corrente per selezionare tutte le voci corrispondenti anziché selezionarle una alla volta.   

> [!div class="mx-imgBorder"]
> ![Connessione Riquadro a comparsa dei messaggi di posta elettronica](_img/connect-emails/connect-emails-flyout.png "Selezionare i sottoscrittori che si desidera associare alle rispettive Azure AD e fare clic su Continua.")

Fare quindi **clic su** Continua per visualizzare un elenco delle modifiche da apportare. Se si accetta, fare **clic su Salva** per apportare le modifiche. Il sottoscrittore riceverà anche un messaggio che informa la modifica al successivo accesso alla sottoscrizione.  Si noti che solo i due sottoscrittori corrispondenti nel Azure Active Directory vengono visualizzati in questo elenco.  In questo esempio, dal momento che Non aveva un indirizzo corrispondente nel Azure AD, il suo account Microsoft (MSA) non è stato abbinato a un account aziendale. 

> [!div class="mx-imgBorder"]
> ![Connessione Conferma dei messaggi di posta elettronica](_img/connect-emails/connect-emails-confirm.png "Fare clic su Continua per implementare le modifiche proposte, quindi fare clic su Salva.") 

> [!NOTE]
> Quando si modifica l'indirizzo di posta elettronica di accesso, viene aggiornato solo il messaggio di posta elettronica usato dal sottoscrittore per accedere alla propria sottoscrizione in https://my.visualstudio.com . Se il sottoscrittore ha già attivato vantaggi come Azure o Pluralsight usando l'altro indirizzo di posta elettronica, dovrà continuare a usare tali indirizzi di posta elettronica per accedervi. Per i nuovi vantaggi a cui accedono, devono usare il nuovo indirizzo di posta elettronica. 

## <a name="support-resources"></a>Risorse di supporto
- Per assistenza per l'amministrazione di Sottoscrizioni di Visual Studio, contattare [Visual Studio supporto per le sottoscrizioni](https://aka.ms/vsadminhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

##  <a name="next-steps"></a>Passaggi successivi
- Dopo aver aggiornato gli indirizzi di posta elettronica dei sottoscrittori, è consigliabile informarli che le informazioni di accesso sono state modificate.  L'utente riceverà anche un messaggio di posta elettronica con le informazioni aggiornate.
- Può essere utile [filtrare l'elenco dei sottoscrittori](search-license.md) nell'organizzazione per cercare gli indirizzi di posta elettronica di accesso che potrebbero dover essere modificati.