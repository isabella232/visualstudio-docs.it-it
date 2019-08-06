---
title: Visualizzazione di Indirizzi di posta elettronica personali in VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori?
ms.openlocfilehash: 8418a177e793f0b4fe9a5019d2cf62fa724312ff
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605762"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Sottoscrizioni di Visual Studio - Perché vengono visualizzati indirizzi Hotmail o Gmail per i sottoscrittori?
Dopo che le società hanno completato la migrazione da Volume Licensing Service Center (VLSC) al nuovo [portale di amministrazione delle sottoscrizioni](https://manage.visualstudio.com) di Visual Studio, gli amministratori hanno notato con sorpresa che per l'indirizzo di posta elettronica di accesso di alcuni sottoscrittori erano indicati indirizzi di terze parti, come Hotmail, Yahoo! o Gmail.  Per altre informazioni, vedere [questo video](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Causa
Questa situazione si verifica a causa dei processi di accesso associati all'esperienza legacy degli abbonati a MSDN. La migrazione degli utenti da Volume License Service Center (VLSC) al portale di amministrazione delle sottoscrizioni di Visual Studio è stata completata senza modifiche. Gli amministratori potrebbero non essere a conoscenza del fatto che gli utenti usavano account personali per accedere ai vantaggi della propria sottoscrizione. Prima delle migrazioni dei sottoscrittori di Visual Studio, completate nel 2016, erano necessarie due azioni per usare correttamente una sottoscrizione di Visual Studio:
1. L'amministratore "assegnava" la sottoscrizione a un singolo sottoscrittore, usando l'indirizzo di posta elettronica dell'account aziendale o dell'istituto di istruzione.
2. Il sottoscrittore "attivava" la sottoscrizione.

Durante il processo di attivazione del sottoscrittore: Era necessario un account Microsoft per accedere. Se il sottoscrittore non tentava di convertire l'account aziendale o dell'istituto di istruzione (ad esempio tasha@contoso.com) in un account Microsoft, poteva creare un nuovo account Microsoft o sfruttarne uno esistente. A causa di tutto ciò, l'indirizzo di posta elettronica di accesso può risultare diverso dall'indirizzo di posta elettronica di assegnazione.

> [!NOTE]
> La nuova esperienza di sottoscrizione in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) supporta i tipi di identità sia con account aziendale o dell'istituto di istruzione sia con account Microsoft.

Infine, poiché per la migrazione degli amministratori sono stati recuperati i dati relativi all'indirizzo di posta elettronica di accesso del nuovo sottoscrittore da VLSC per completare la nuova esperienza di gestione dei sottoscrittori, gli amministratori di cui è stata eseguita la migrazione di recente potrebbero aver notato questi account personali, passati inosservati in precedenza, a causa delle modifiche apportate all'interfaccia utente che hanno reso più visibili queste informazioni.

## <a name="solution"></a>Soluzione
Per risolvere il problema, è necessario modificare le informazioni sui sottoscrittori per aggiornare i relativi indirizzi di posta elettronica di accesso.  È possibile apportare le modifiche per singoli sottoscrittori o in blocco. Per informazioni complete, vedere [Modificare una sottoscrizione](edit-license.md).

##  <a name="next-steps"></a>Passaggi successivi
- Dopo aver aggiornato gli indirizzi di posta elettronica dei sottoscrittori, è consigliabile informarli che le informazioni di accesso sono state modificate.  L'utente riceverà anche un messaggio di posta elettronica con le informazioni aggiornate.
- Può essere utile [filtrare l'elenco dei sottoscrittori](search-license.md) nell'organizzazione per cercare gli indirizzi di posta elettronica di accesso che potrebbero dover essere modificati.  

