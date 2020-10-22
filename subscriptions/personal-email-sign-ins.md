---
title: Visualizzazione di Indirizzi di posta elettronica personali in VLSC
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 09/22/2020
ms.topic: conceptual
description: Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori?
ms.openlocfilehash: dc2de6c852f39f789fb07358384ad490d13f137c
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "91022656"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Sottoscrizioni di Visual Studio: perché vengono visualizzati gli account personali per i sottoscrittori?
Dopo la migrazione delle aziende da Volume Licensing Service Center (VLSC) al nuovo portale di [amministrazione delle sottoscrizioni](https://manage.visualstudio.com)di Visual Studio, gli amministratori sono sorpresi di scoprire che l'indirizzo di posta elettronica di accesso per alcuni sottoscrittori Mostra un indirizzo di posta elettronica personale come Hotmail o Outlook.  

## <a name="cause"></a>Causa
Questa situazione si verifica a causa dei processi di accesso associati all'esperienza legacy degli abbonati a MSDN. La migrazione degli utenti da Volume License Service Center (VLSC) al portale di amministrazione delle sottoscrizioni di Visual Studio è stata completata senza modifiche. Gli amministratori potrebbero non essere a conoscenza del fatto che gli utenti usavano account personali per accedere ai vantaggi della propria sottoscrizione. Prima delle migrazioni dei sottoscrittori di Visual Studio, completate nel 2016, erano necessarie due azioni per usare correttamente una sottoscrizione di Visual Studio:
1. L'amministratore "assegnava" la sottoscrizione a un singolo sottoscrittore, usando l'indirizzo di posta elettronica dell'account aziendale o dell'istituto di istruzione.
2. Il sottoscrittore "attivava" la sottoscrizione.

Durante il processo di attivazione del sottoscrittore, veniva richiesto un account Microsoft per eseguire l'accesso. Se il sottoscrittore non tentava di convertire l'account aziendale o dell'istituto di istruzione (ad esempio tasha@contoso.com) in un account Microsoft, poteva creare un nuovo account Microsoft o sfruttarne uno esistente. A causa di tutto ciò, l'indirizzo di posta elettronica di accesso può risultare diverso dall'indirizzo di posta elettronica di assegnazione.

> [!NOTE]
> L'esperienza del Sottoscrittore moderna di [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) supporta sia i tipi di identità dell'account aziendale che dell'Istituto di istruzione Microsoft (MSA).

## <a name="solution"></a>Soluzione
Per risolvere il problema, è sufficiente selezionare il pulsante **Connetti messaggi di posta elettronica** e il sistema tenterà di associare gli account di MSAS agli utenti esistenti nell'Azure Active Directory dell'organizzazione (Azure ad) in base alla corrispondenza con il nome e il cognome. Se si verifica un errore, è possibile rimuovere qualsiasi corrispondenza facendo clic sulla **X** a destra della corrispondenza.  

Guarda questo video o continua a leggere per scoprire come risolverlo. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![Pulsante Connetti messaggi di posta elettronica](_img/connect-emails/connect-emails-button.png "Fare clic su Connetti messaggi di posta elettronica per trovare la corrispondenza con gli utenti con account Microsoft per il Azure Active Directory")

È anche possibile usare la **directory di ricerca** per correggere gli errori o inserire le informazioni mancanti dal Azure ad. Se l'aspetto di tutte le corrispondenze è corretto, è possibile scegliere il pulsante **identità corrente** per selezionare tutte le voci corrispondenti anziché selezionarle una alla volta.  

> [!div class="mx-imgBorder"]
> ![Connessione al volo](_img/connect-emails/connect-emails-flyout.png "Selezionare i sottoscrittori di cui si desidera trovare la corrispondenza con le identità Azure AD e fare clic su continua.")

Fare quindi clic su **continue (continua** ) per passare a un elenco delle modifiche da eseguire. Se si accetta, fare clic su **Salva** e verranno apportate le modifiche. Il sottoscrittore riceverà anche un messaggio che li informa della modifica al successivo accesso alla sottoscrizione.  Si noti che in questo elenco vengono visualizzati solo i due Sottoscrittori che corrispondono all'Azure Active Directory.  In questo esempio, poiché Frederick non ha un indirizzo corrispondente nella Azure AD, il suo account Microsoft (MSA) non corrisponde a un account aziendale. 

> [!div class="mx-imgBorder"]
> ![Conferma connessione messaggi di posta elettronica](_img/connect-emails/connect-emails-confirm.png "Fare clic su continua per implementare le modifiche proposte, quindi fare clic su Salva.") 

> [!NOTE]
> Quando si modifica l'indirizzo di posta elettronica di accesso, questo aggiorna solo il messaggio di posta elettronica usato dal Sottoscrittore per accedere alla sottoscrizione in https://my.visualstudio.com . Se il Sottoscrittore ha già attivato vantaggi come Azure o Pluralsight usando l'altro indirizzo di posta elettronica, sarà necessario continuare a usare tali indirizzi di posta elettronica per accedervi. Per tutti i nuovi vantaggi a cui hanno accesso, è necessario usare il nuovo indirizzo di posta elettronica. 

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

##  <a name="next-steps"></a>Passaggi successivi
- Dopo aver aggiornato gli indirizzi di posta elettronica dei sottoscrittori, è consigliabile informarli che le informazioni di accesso sono state modificate.  L'utente riceverà anche un messaggio di posta elettronica con le informazioni aggiornate.
- Può essere utile [filtrare l'elenco dei sottoscrittori](search-license.md) nell'organizzazione per cercare gli indirizzi di posta elettronica di accesso che potrebbero dover essere modificati.