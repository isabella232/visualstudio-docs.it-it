---
title: Visualizzazione di Indirizzi di posta elettronica personali in VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori?
ms.openlocfilehash: c4a3202bfb14246fa8057309de90bdc7c32db5df
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410216"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori?
Dopo che le società hanno completato la migrazione da Volume Licensing Service Center (VLSC) al nuovo [portale di amministrazione delle sottoscrizioni](https://manage.visualstudio.com) di Visual Studio, gli amministratori hanno notato con sorpresa che per l'indirizzo di posta elettronica di accesso di alcuni sottoscrittori erano indicati indirizzi di terze parti, come Hotmail, Yahoo! o Gmail.  Per altre informazioni, vedere [questo video](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Causa
Questa situazione si verifica a causa dei processi di accesso associati all'esperienza legacy degli abbonati a MSDN. La migrazione degli utenti da Volume License Service Center (VLSC) al portale di amministrazione delle sottoscrizioni di Visual Studio è stata completata senza modifiche. Gli amministratori potrebbero non essere a conoscenza del fatto che gli utenti usavano account personali per accedere ai vantaggi della propria sottoscrizione. Prima delle migrazioni dei sottoscrittori di Visual Studio, completate nel 2016, erano necessarie due azioni per usare correttamente una sottoscrizione di Visual Studio:
1. L'amministratore "assegnava" la sottoscrizione a un singolo sottoscrittore, usando l'indirizzo di posta elettronica dell'account aziendale o dell'istituto di istruzione.
2. Il sottoscrittore "attivava" la sottoscrizione.

Durante il processo di attivazione del sottoscrittore, veniva richiesto un account Microsoft per eseguire l'accesso. Se il sottoscrittore non tentava di convertire l'account aziendale o dell'istituto di istruzione (ad esempio tasha@contoso.com) in un account Microsoft, poteva creare un nuovo account Microsoft o sfruttarne uno esistente. A causa di tutto ciò, l'indirizzo di posta elettronica di accesso può risultare diverso dall'indirizzo di posta elettronica di assegnazione.

> [!NOTE]
> La nuova esperienza di sottoscrizione in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) supporta i tipi di identità sia con account aziendale o dell'istituto di istruzione sia con account Microsoft.

## <a name="solution"></a>Soluzione
Per risolvere il problema, è sufficiente selezionare il pulsante **Connetti messaggi di posta elettronica** e il sistema tenterà di associare gli account di MSAS agli utenti esistenti nell'Azure Active Directory dell'organizzazione (Azure ad) in base alla corrispondenza con il nome e il cognome. Se si verifica un errore, è possibile rimuovere qualsiasi corrispondenza facendo clic sulla **X** a destra della corrispondenza.  

> [!div class="mx-imgBorder"]
> Pulsante di ![Connect email](_img/connect-emails/connect-emails-button.png)

È anche possibile usare la **directory di ricerca** per correggere gli errori o inserire le informazioni mancanti dal Azure ad. Se l'aspetto di tutte le corrispondenze è corretto, è possibile scegliere "Seleziona tutti i sottoscrittori corrispondenti", anziché selezionarli uno alla volta.  

> [!div class="mx-imgBorder"]
> ](_img/connect-emails/connect-emails-flyout.png) di ![per il collegamento di posta elettronica

Fare quindi clic su "continua" per passare a una schermata che descrive le modifiche da eseguire. Se si accetta, fare clic su "Salva" per apportare le modifiche. Il sottoscrittore riceverà anche un messaggio che li informa della modifica al successivo accesso alla sottoscrizione.   

> [!div class="mx-imgBorder"]
> Conferma ![di connessione messaggi di posta elettronica](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Quando si modifica l'indirizzo di posta elettronica di accesso, questo aggiorna solo il messaggio di posta elettronica usato per accedere alla propria sottoscrizione in https://my.visualstudio.com. Se il Sottoscrittore ha già attivato vantaggi come Azure o Pluralsight usando l'altro indirizzo di posta elettronica, sarà necessario continuare a usare tali indirizzi di posta elettronica per accedervi. Per tutti i nuovi vantaggi a cui hanno accesso, è necessario usare il nuovo indirizzo di posta elettronica. 

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Passaggi successivi
- Dopo aver aggiornato gli indirizzi di posta elettronica dei sottoscrittori, è consigliabile informarli che le informazioni di accesso sono state modificate.  L'utente riceverà anche un messaggio di posta elettronica con le informazioni aggiornate.
- Può essere utile [filtrare l'elenco dei sottoscrittori](search-license.md) nell'organizzazione per cercare gli indirizzi di posta elettronica di accesso che potrebbero dover essere modificati.  
