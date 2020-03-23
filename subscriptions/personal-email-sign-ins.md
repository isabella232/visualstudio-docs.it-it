---
title: Visualizzazione di Indirizzi di posta elettronica personali in VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 03/17/2020
ms.topic: conceptual
description: Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori?
ms.openlocfilehash: 7cd6a4761efb7dcad7568bd0a95ba33141407055
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "79550328"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Sottoscrizioni di Visual Studio: perché vengono visualizzati gli account personali per i sottoscrittori?
Dopo la migrazione delle società dal Volume Licensing Service Center (VLSC) al nuovo portale di [amministrazione delle sottoscrizioni](https://manage.visualstudio.com)di Visual Studio , gli amministratori sono stati sorpresi di scoprire che l'"Indirizzo di posta elettronica di accesso" per alcuni sottoscrittori mostra un indirizzo di posta elettronica personale come Hotmail o Outlook.  Per altre informazioni, vedere [questo video](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Causa
Questa situazione si verifica a causa dei processi di accesso associati all'esperienza legacy degli abbonati a MSDN. La migrazione degli utenti da Volume License Service Center (VLSC) al portale di amministrazione delle sottoscrizioni di Visual Studio è stata completata senza modifiche. Gli amministratori potrebbero non essere a conoscenza del fatto che gli utenti usavano account personali per accedere ai vantaggi della propria sottoscrizione. Prima delle migrazioni dei sottoscrittori di Visual Studio, completate nel 2016, erano necessarie due azioni per usare correttamente una sottoscrizione di Visual Studio:
1. L'amministratore "assegnava" la sottoscrizione a un singolo sottoscrittore, usando l'indirizzo di posta elettronica dell'account aziendale o dell'istituto di istruzione.
2. Il sottoscrittore "attivava" la sottoscrizione.

Durante il processo di attivazione del sottoscrittore, veniva richiesto un account Microsoft per eseguire l'accesso. Se il sottoscrittore non tentava di convertire l'account aziendale o dell'istituto di istruzione (ad esempio tasha@contoso.com) in un account Microsoft, poteva creare un nuovo account Microsoft o sfruttarne uno esistente. A causa di tutto ciò, l'indirizzo di posta elettronica di accesso può risultare diverso dall'indirizzo di posta elettronica di assegnazione.

> [!NOTE]
> La moderna esperienza [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) di sottoscrittore supporta i tipi di identità di lavoro, scuola e account Microsoft (MSA).

## <a name="solution"></a>Soluzione
Per risolvere il problema, è sufficiente selezionare il pulsante Connetti messaggi di **posta elettronica** e il sistema tenterà di associare gli account con MSA agli utenti esistenti in Azure Active Directory (Azure AD) dell'organizzazione in base alla corrispondenza tra nome e cognome. Se c'è un errore, è possibile rimuovere qualsiasi corrispondenza facendo clic sulla **X** a destra della partita.  

> [!div class="mx-imgBorder"]
> ![Pulsante Connetti e-mail](_img/connect-emails/connect-emails-button.png)

È anche possibile usare la **directory di ricerca** per correggere gli errori o immettere informazioni mancanti da Azure AD. Se tutte le corrispondenze sono corrette, puoi scegliere di "Selezionare tutti i sottoscrittori corrispondenti", invece di selezionarli uno alla volta.  

> [!div class="mx-imgBorder"]
> ![Connetti e-mail a comparsa](_img/connect-emails/connect-emails-flyout.png)

Poi clicca su "continua" che ti porterà a una schermata che delinea le modifiche da prendere posto. Se si accetta, fare clic su "Salva" e le modifiche verranno apportate. Il sottoscrittore riceverai anche un messaggio che li informa della modifica al successivo accesso alla sottoscrizione.   

> [!div class="mx-imgBorder"]
> ![Conferma del collegamento delle e-mail](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Quando si modifica l'indirizzo di posta elettronica di accesso, viene aggiornato https://my.visualstudio.comsolo il messaggio di posta elettronica utilizzato dal sottoscrittore per accedere alla sottoscrizione in . Se il sottoscrittore ha già attivato i vantaggi, ad esempio Azure o Pluralsight usando l'altro indirizzo di posta elettronica, dovrà continuare a usare tali indirizzi di posta elettronica per accedervi. Per tutti i nuovi vantaggi a cui accedono, è necessario utilizzare il nuovo indirizzo di posta elettronica. 

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Passaggi successivi
- Dopo aver aggiornato gli indirizzi di posta elettronica dei sottoscrittori, è consigliabile informarli che le informazioni di accesso sono state modificate.  L'utente riceverà anche un messaggio di posta elettronica con le informazioni aggiornate.
- Può essere utile [filtrare l'elenco dei sottoscrittori](search-license.md) nell'organizzazione per cercare gli indirizzi di posta elettronica di accesso che potrebbero dover essere modificati.  
