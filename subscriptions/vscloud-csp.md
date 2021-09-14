---
title: Acquisto di sottoscrizioni cloud di Visual Studio per i CSP
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: d2ab13ed-ef79-4ef0-8736-eccd04bc6020
ms.date: 03/18/2021
ms.topic: conceptual
description: Informazioni sulle modalità di acquisto e di gestione delle sottoscrizioni cloud di Visual Studio per Cloud Solution Provider.
ms.openlocfilehash: 09c905d113920a0bb55aed8851d3fb62c92a39bf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709978"
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Acquistare e gestire sottoscrizioni cloud di Visual Studio per i clienti
I partner inclusi nel programma [Cloud Solution Provider (CSP)](https://partner.microsoft.com/cloud-solution-provider) possono acquistare sottoscrizioni cloud di Visual Studio Enterprise e Visual Studio Professional per i loro clienti.

[Confrontare le opzioni di sottoscrizione cloud](https://visualstudio.microsoft.com/vs/pricing)

> [!NOTE]
> Microsoft non offre più sottoscrizioni annuali di Visual Studio Professional e Visual Studio Enterprise nelle sottoscrizioni cloud. Non verrà apportata alcuna modifica all'esperienza dei clienti corrente, né alle possibilità di rinnovo, espansione, riduzione o annullamento delle sottoscrizioni esistenti. I nuovi clienti sono invitati a passare [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) a per esplorare diverse opzioni per l'acquisto Visual Studio.

## <a name="prerequisites"></a>Prerequisiti
È prima di tutto necessario configurare il tenant del cliente nel Centro per i partner e creare una sottoscrizione di Azure per questo tenant.

[Scopri di più](/azure/devops/organizations/billing/csp/set-up-csp-customer)

## <a name="who-can-buy-visual-studio-subscriptions"></a>Chi può acquistare sottoscrizioni di Visual Studio?
Chiunque disponga dell'[accesso come Proprietario o Collaboratore](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fvsts%2Forganizations%2Fbilling%2Fadd-backup-billing-managers%3Fview%3Dvsts%2520%2520sa&data=02%7C01%7C%7Cb9e717e8abff47b0cd7e08d618edd860%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636723807145220358&sdata=aIaamEXHhx94KCYVY%2FFibqFzNBEqKPntpql867xAMgU%3D&reserved=0) per la sottoscrizione di Azure può acquistare sottoscrizioni di Visual Studio.

## <a name="how-to-buy"></a>Modalità di acquisto

1. Accedere al [Centro per i partner Microsoft](https://partnercenter.microsoft.com).
0. Scegliere **Clienti** e selezionare un cliente per cui effettuare l'acquisto.
0. Scegliere **Gestione dei servizi**.
0. Scegliere **Visual Studio Marketplace**.
0. Assicurarsi che sia visualizzato il nome del cliente nell'angolo in alto a destra.
0. Scegliere **Sottoscrizioni.**
0. Scegliere Enterprise o Professional per Visual Studio.
0. Scegliere **Acquista**.
0. Scegliere la sottoscrizione di Azure per la fatturazione dell'acquisto.
0. Immettere il numero di utenti necessari per il cliente.
0. Rivedi l'ordine e **Conferma** esso.

>[!NOTE]
> È necessario seguire questa procedura ogni volta che si acquistano sottoscrizioni di Visual Studio come CSP. Al momento non è disponibile alcuna API per automatizzare l'acquisto.

Dopo aver confermato l'acquisto, è possibile scegliere **Gestisci** per assegnare le sottoscrizioni agli utenti finali del cliente.  È anche possibile accedere al portale di amministrazione della sottoscrizione dal Partner Center scegliendo **Gestione dei servizi.**  Da qui, vedere i passaggi o il video seguenti.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Come gestire le sottoscrizioni cloud di Visual Studio per il cliente

1. Accedere al [Centro per i partner Microsoft](https://partnercenter.microsoft.com).
0. Scegliere **Clienti** e il nome del cliente.
0. Scegliere **Gestione dei servizi**.
0. Scegliere **Gestisci sottoscrizioni di Visual Studio**.

Se è disponibile più di una sottoscrizione di Azure per il cliente, usare il menu a discesa per scegliere la sottoscrizione di Azure tramite la quale sono stati effettuati gli acquisti.  In **Riepilogo licenze** viene visualizzato il numero di sottoscrizioni assegnate e disponibili per ogni opzione di sottoscrizione cloud di Visual Studio.  Il riepilogo consente anche di acquistare sottoscrizioni aggiuntive o ridurre il numero di sottoscrizioni.

Scegliere **Aggiungi** per assegnare una sottoscrizione a un nuovo utente.  Il conteggio visualizzato viene aggiornato e l'utente finale riceve una notifica tramite posta elettronica. L'utente finale può quindi accedere con l'indirizzo di posta elettronica fornito per attivare la sottoscrizione di Visual Studio nel [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

Per riassegnare una sottoscrizione di Visual Studio a un altro utente, è possibile eliminare la sottoscrizione corrente e aggiungere un nuovo sottoscrittore.

Se un sottoscrittore non ha ancora attivato la sottoscrizione di Visual Studio, è possibile che non abbia ricevuto il messaggio di posta elettronica di invito.  È possibile usare il portale di amministrazione di Visual Studio anche per richiedere un nuovo invio dell'invito per l'attivazione all'utente.

## <a name="view-visual-studio-pricing-for-csp-partners"></a>Visualizzare i prezzi di Visual Studio per i partner CSP
Per visualizzare i prezzi di Visual Studio per i partner CSP, accedere al [Centro per i partner](https://partnercenter.microsoft.com).  Scegliere **Prezzi e offerte** nella struttura di spostamento a sinistra.  Scegliere il file dei prezzi per il mese in corso in **servizi basati sull'utilizzo di servizi** in alto a destra. Nel foglio di calcolo di Excel scaricato passare al foglio **Azure Price List** (Listino prezzi di Azure) e selezionare **Visual Studio** per filtrare la colonna **Meter Category** (Categoria misuratore).

Di seguito viene illustrato come interpretare le informazioni disponibili in questo foglio di calcolo:

| Categoria del contatore    |   Nome                 |  Unità                                |           Contenuto                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Visual Studio     | Enterprise             |  Subscription                         | Sottoscrizione mensile di Visual Studio Enterprise   |
| Visual Studio     | Professionale           |  Subscription                         | Sottoscrizione mensile di Visual Studio Professional |

Offriamo uno sconto del 5% per la sesta unità acquistata (per un determinato cliente) mensilmente di ogni sottoscrizione di Visual Studio. Questo è il motivo per cui sono visualizzate due righe per ogni opzione di sottoscrizione. Una riga mostra un valore minimo pari a 0, da interpretare come prezzo di base per le unità da 1 a 5. L'altra riga mostra un valore minimo pari a 5, ovvero il prezzo scontato del % 5 che si applica dalle 6 unità in poi.

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>D: come vengono elaborati gli addebiti per le sottoscrizioni cloud **mensili**?
R: al momento del primo acquisto, viene fatturata una quantità ripartita in base ai giorni rimanenti del mese corrente. Ad esempio, se si acquistano 10 sottoscrizioni cloud mensili di Visual Studio Professional il 15 aprile, vengono addebitate 5 unità perché rimangono 15 giorni del mese di 30 giorni, ovvero il 50%, quindi l'addebito delle unità viene ripartito al 50%. Il primo del mese di maggio e per ogni mese successivo fino all'annullamento, verranno fatturate tutte e 10 le unità.

Quando si aumenta la quantità a pagamento in un secondo momento, anche le unità aggiunte verranno ripartite in base ai giorni rimanenti del mese corrente. Pertanto, se si acquista un'altra sottoscrizione cloud mensile di Visual Studio Professional il 10 maggio, verranno fatturate approssimativamente 0,677 unità (21 giorni rimanenti nel mese di maggio di 31 giorni).

### <a name="q-how-do-cancellations-work"></a>D: come funzionano gli annullamenti?
R: quando si annulla una sottoscrizione cloud di Visual Studio, si annulla il rinnovo automatico. La sottoscrizione continua fino alla relativa data di rinnovo normale e poi semplicemente scade. Alla scadenza, il sottoscrittore di Visual Studio non può più usare Visual Studio o qualsiasi altro vantaggio dalla sottoscrizione.

Con le sottoscrizioni cloud mensili, gli annullamenti diventano effettivi a partire dal primo giorno del mese successivo. Se si annullano solo alcune delle sottoscrizioni cloud mensili del cliente, assicurarsi di rimuovere gli utenti il primo del mese successivo per assicurarsi che rimangano assegnate sottoscrizioni attive alle persone corrette.

Per le sottoscrizioni cloud annuali, gli annullamenti diventano effettivi il primo giorno del mese successivo a 12 mesi dall'acquisto originale o a 12 mesi dall'ultimo addebito per il rinnovo annuale. Ad esempio, se si acquista una sottoscrizione cloud annuale di Visual Studio Enterprise il 3 gennaio 2018, questa rimane attiva fino al 1 febbraio 2019 quando viene rinnovata automaticamente per un altro anno. Se si annulla la sottoscrizione in qualsiasi momento tra tale data e il 1 febbraio 2020, la scadenza sarà il 1 febbraio 2020. Non è previsto alcuno sconto in caso di annullamento di sottoscrizioni cloud annuali prima del termine dell'anno di validità.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>D: quali tipi di sconti per volume sono disponibili per le sottoscrizioni di Visual Studio?
R: viene offerto uno sconto del 5% oltre le 6 sottoscrizioni *per ogni tipo* di sottoscrizione:
- Visual Studio Professional (mensile)
- Visual Studio Enterprise (mensile)

Ad esempio, quindi, se si acquistano 6 sottoscrizioni mensili di Visual Studio Professional e 5 sottoscrizioni mensili di Visual Studio Enterprise, si paga il prezzo normale per le 5 sottoscrizioni Professional, si ottiene uno sconto del 5% per la sesta sottoscrizione Professional e si paga il prezzo normale per tutte le 5 sottoscrizioni Enterprise.

Inoltre, lo sconto è valido solo per gli addebiti in un determinato periodo di fatturazione mensile. Pertanto, se si acquistano 5 sottoscrizioni annuali di Visual Studio Professional in un mese e quindi se ne acquistano altre 5 nel mese successivo, verrà applicato il prezzo normale per tutte le dieci sottoscrizioni.

Questi sconti sono indicati nei dati sui prezzi all'interno del [Centro per i partner](https://partnercenter.microsoft.com).

### <a name="q-are-there-renewal-discounts"></a>D: sono previsti sconti per il rinnovo?
R: no, i prezzi per le sottoscrizioni di Visual Studio sono fissi. Lo stesso prezzo viene applicato per le nuove sottoscrizioni e per i rinnovi.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>D: esistono opzioni per i prezzi di Azure per sviluppo/test per i CSP?
 R: attualmente non è possibile. I clienti possono sfruttare i [Prezzi di Azure per sviluppo/test](https://azure.microsoft.com/pricing/dev-test/), ma non è disponibile alcuna offerta specifica per i CSP.

## <a name="resources"></a>Risorse
- Per assistenza su vendite, sottoscrizioni, account e fatturazione per Sottoscrizioni di Visual Studio, vedere Supporto Visual Studio [sottoscrizioni](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Per le risposte alle domande frequenti sulla fatturazione, vedere le domande frequenti sulla fatturazione nel [cloud.](vscloud-billing-faq.yml)