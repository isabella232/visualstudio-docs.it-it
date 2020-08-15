---
title: Domande frequenti sulla fatturazione per le sottoscrizioni cloud di Visual Studio Enterprise e Visual Studio Professional
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 21e0471d-ad59-4d21-9c6f-13f7147569af
ms.date: 03/24/2020
ms.topic: conceptual
description: Domande sulla fatturazione per sottoscrizioni cloud.
ms.openlocfilehash: d09d9d4a3b21d0b96f0664451323dcc523d73cb3
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249383"
---
# <a name="visual-studio-cloud-subscriptions-billing-faq"></a>Domande frequenti sulla fatturazione per le sottoscrizioni cloud di Visual Studio
Assicurarsi di [confrontare i vantaggi e i prezzi delle sottoscrizioni cloud](https://visualstudio.microsoft.com/vs/pricing/) per comprendere i vantaggi di ogni sottoscrizione di Visual Studio, esaminando le differenze tra le sottoscrizioni cloud e standard di Visual Studio, i dettagli dei vantaggi per i sottoscrittori e altri aspetti.

## <a name="general-purchasing-questions"></a>Domande generali sull'acquisto
### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-using-a-purchase-order"></a>D: è possibile acquistare sottoscrizioni cloud di Visual Studio usando un ordine di acquisto?
R: No. Tutte le sottoscrizioni cloud di Visual Studio devono essere acquistate usando una sottoscrizione di Azure. (Considerarla come l'account di fatturazione di Azure.)

### <a name="q-what-types-of-azure-subscriptions-can-be-used-to-buy-visual-studio-cloud-subscriptions"></a>D: quali tipi di sottoscrizioni di Azure possono essere usati per acquistare sottoscrizioni cloud di Visual Studio?
R: possono essere usate quasi tutte le sottoscrizioni di Azure. Sono supportate le sottoscrizioni di Azure collegate a [Enterprise Agreement (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/), le sottoscrizioni di Azure configurate da Cloud Solution Provider (CSP), le sottoscrizioni di Azure configurate da rivenditori di Microsoft Open License e le sottoscrizioni di Azure con pagamento in base al consumo.

Non possono essere usati alcuni tipi di sottoscrizioni di Azure, tra cui la [versione di valutazione gratuita di Azure](https://azure.microsoft.com/pricing/free-trial/) e sottoscrizioni incluse come vantaggi per i sottoscrittori nelle sottoscrizioni di Visual Studio.

### <a name="q-am-i-required-to-buy-other-azure-services"></a>D: è obbligatorio acquistare altri servizi di Azure?
R: assolutamente no. Se si vogliono acquistare solo sottoscrizioni cloud di Visual Studio tramite Azure, è possibile farlo.

## <a name="enterprise-agreement-ea-customers"></a>Clienti Enterprise Agreement (EA)
### <a name="q-can-i-use-an-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>D: è possibile usare un contratto Enterprise Agreement per acquistare sottoscrizioni cloud di Visual Studio?
R: sì. È necessario essere un proprietario o collaboratore per una sottoscrizione di Azure creata per il contratto EA. Assicurarsi di effettuare gli acquisti di sottoscrizioni cloud di Visual Studio direttamente in Visual Studio Marketplace. Non è possibile acquistare sottoscrizioni cloud di Visual Studio usando un ordine di acquisto.

### <a name="q-how-can-i-tell-whether-i-have-the-necessary-privileges-to-buy-services-in-the-visual-studio-marketplace-through-my-organizations-enterprise-agreement"></a>D: come è possibile stabilire se sono disponibili i privilegi necessari per acquistare i servizi in Visual Studio Marketplace tramite il contratto Enterprise Agreement dell'organizzazione?
R: l'approccio più semplice per determinare se si dispone dei privilegi appropriati è quello di selezionare il pulsante **Acquista** per un servizio offerto nella Visual Studio Marketplace.
È necessario selezionare una sottoscrizione di Azure (ovvero un account di fatturazione) dall'elenco presentato di sottoscrizioni di Azure attualmente collegate all'account di accesso.
Dato che il nome della sottoscrizione di Azure include per impostazione predefinita il tipo di account di fatturazione ("Pagamento a consumo", "Contratto Enterprise Agreement" e così via), spesso è chiaro se la sottoscrizione di Azure fa parte del contratto Enterprise Agreement.

Un altro approccio consiste nel provare a visitare [Azure Enterprise Portal](https://ea.azure.com).  Se è possibile accedere a questo portale, si ha già il ruolo di amministratore dell'organizzazione o di proprietario dell'account. Solo i proprietari di account possono configurare nuovi account di fatturazione Azure in un contratto Enterprise Agreement. Se non si ha accesso ad Azure Enterprise Portal, scoprire chi è l'amministratore dell'organizzazione e chiedere a tale persona di essere aggiunti come proprietario dell'account in Azure Enterprise Portal.  Se non si riesce a trovare questa persona, è possibile [inviare un ticket di supporto](https://support.microsoft.com/supportrequestform/cf791efa-485b-95a3-6fad-3daf9cd4027c) e richiedere le informazioni di contatto.  Per il ticket di supporto sono necessari il nome dell'organizzazione e il numero di registrazione del contratto Enterprise Agreement.

### <a name="q-can-i-use-the-azure-monetary-commitment-funds-from-my-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>R: è possibile usare i fondi degli impegni monetari di Azure dal contratto Enterprise Agreement per acquistare sottoscrizioni cloud di Visual Studio?
R: no, questi fondi prepagati non sono idonei per l'acquisto di sottoscrizioni cloud di Visual Studio. Quando si sceglie una sottoscrizione di Azure creata per il contratto Enterprise Agreement per l'acquisto di sottoscrizioni cloud di Visual Studio, i costi compariranno nella fattura successiva per le "eccedenze". In genere questo accade ogni mese, ma a causa di regole storiche per alcuni clienti Enterprise Agreement, è possibile che la fattura per le eccedenze non venga emessa per diversi mesi. Consultare un esperto di gestione delle licenze per il contratto EA se è necessario conoscere la quantità di acquisti aggiuntivi (acquisti non idonei per i fondi degli impegni monetari di Azure) che causerà l'emissione di una fattura per le eccedenze.

## <a name="how-charges-are-processed"></a>Modalità di elaborazione degli addebiti
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>D: come vengono elaborati gli addebiti per le sottoscrizioni cloud **mensili**?
R: al momento del primo acquisto, viene fatturata una quantità ripartita in base ai giorni rimanenti del mese corrente. Ad esempio, nel caso di un acquisto di 10 sottoscrizioni cloud mensili di Visual Studio Professional effettuato il 15 aprile, vengono addebitate 5 unita perché rimane il 50% del mese (15 giorni in un mese di 30 giorni).
Il primo del mese di maggio e per ogni mese successivo fino all'annullamento, verranno fatturate tutte e 10 le unità.

Quando si aumenta la quantità a pagamento in un secondo momento, anche le unità aggiunte verranno ripartite in base ai giorni rimanenti del mese corrente. Pertanto, se si acquista un'altra sottoscrizione cloud mensile di Visual Studio Professional il 10 maggio, verranno fatturate approssimativamente 0,677 unità (21 giorni rimanenti nel mese di maggio di 31 giorni).

### <a name="q-how-are-annual-cloud-subscription-charges-processed"></a>D: come vengono elaborati gli addebiti per le sottoscrizioni cloud **annuali**?
R: a ogni acquisto viene fatturata immediatamente l'intera quantità acquistata. Gli addebiti non vengono distribuiti nell'anno e non è prevista alcuna ripartizione proporzionale. Se si acquistano sottoscrizioni cloud annuali in momenti diversi nell'anno, ci saranno sottoscrizioni con rinnovo in mesi diversi. Non viene allineata la data di scadenza di tutte le sottoscrizioni cloud annuali di un cliente come avviene comunemente con i contratti multilicenza Microsoft.

### <a name="q-how-do-cancelations-work"></a>D: come funzionano gli annullamenti?
R: quando si annulla una sottoscrizione cloud di Visual Studio, si annulla il rinnovo automatico. La sottoscrizione continua fino alla relativa data di rinnovo normale e poi semplicemente scade.
Alla scadenza, il sottoscrittore di Visual Studio non può più usare Visual Studio o qualsiasi altro vantaggio dalla sottoscrizione.

Con le sottoscrizioni cloud mensili, gli annullamenti diventano effettivi a partire dal primo giorno del mese successivo. Se si annullano solo alcune delle sottoscrizioni cloud mensili, assicurarsi di rimuovere gli utenti il primo del mese successivo per assicurarsi che le sottoscrizioni attive vengano assegnate agli utenti corretti.

Per le sottoscrizioni cloud annuali, gli annullamenti diventano effettivi il primo giorno del mese successivo a 12 mesi dall'acquisto originale o a 12 mesi dall'ultimo addebito per il rinnovo annuale. Ad esempio, se si acquista una sottoscrizione cloud annuale di Visual Studio Professional il 3 gennaio 2018, questa rimane attiva fino al 1° febbraio 2019, quando viene rinnovata automaticamente per un altro anno. Se si annulla la sottoscrizione in qualsiasi momento tra tale data e il 1 febbraio 2020, la scadenza sarà il 1 febbraio 2020. Non è previsto alcuno sconto in caso di annullamento di sottoscrizioni cloud annuali prima del termine dell'anno di validità.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>D: quali tipi di sconti per volume sono disponibili per le sottoscrizioni di Visual Studio?
R: viene offerto uno sconto del 5% oltre le 6 sottoscrizioni *per ogni tipo* di sottoscrizione:

* Visual Studio Professional (mensile)
* Visual Studio Professional (annuale)
* Visual Studio Enterprise (mensile)
* Visual Studio Enterprise (annuale)

Ad esempio, quindi, se si acquistano 6 sottoscrizioni mensili di Visual Studio Professional e 5 sottoscrizioni mensili di Visual Studio Enterprise, si paga il prezzo normale per le 5 sottoscrizioni Professional, si ottiene uno sconto del 5% per la sesta sottoscrizione Professional e si paga il prezzo normale per tutte le 5 sottoscrizioni Enterprise.

Inoltre, lo sconto è valido solo per gli addebiti in un determinato periodo di fatturazione mensile. Pertanto, se si acquistano 5 sottoscrizioni annuali di Visual Studio Professional in un mese e quindi se ne acquistano altre 5 nel mese successivo, verrà applicato il prezzo normale per tutte le 10 sottoscrizioni.

> [!NOTE]
> Microsoft non offre più sottoscrizioni annuali di Visual Studio Professional e Visual Studio Enterprise nelle sottoscrizioni cloud. Non verrà apportata alcuna modifica all'esperienza dei clienti corrente, né alle possibilità di rinnovo, espansione, riduzione o annullamento delle sottoscrizioni esistenti. I nuovi clienti sono invitati a passare a [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) per esplorare diverse opzioni per l'acquisto di Visual Studio.

## <a name="other-questions"></a>Altre domande
### <a name="q-can-i-use-the-monthly-azure-devtest-individual-credit-as-a-visual-studio-subscriber-to-buy-more-visual-studio-cloud-subscriptions"></a>D: è possibile usare il credito individuale Azure DevTest mensile come Sottoscrittore di Visual Studio per acquistare altre sottoscrizioni cloud di Visual Studio?
R: No, non puoi usare il tuo [credito mensile di Azure DevTest individualmente](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) come Sottoscrittore di Visual Studio per pagare gli acquisti Visual Studio Marketplace. Tutti gli acquisti di sottoscrizioni cloud di Visual Studio verranno addebitati sulla carta di credito.
Prima di effettuare acquisti, sarà necessario [rimuovere il limite di spesa](https://azure.microsoft.com/pricing/spending-limits/).

### <a name="q-whats-the-difference-between-annual-and-monthly-cloud-subscriptions"></a>D: qual è la differenza tra sottoscrizioni cloud annuali e mensili?
R: le sottoscrizioni cloud mensili includono Visual Studio oltre all'uso di Azure DevOps Services e TFS. Le sottoscrizioni cloud annuali hanno anche questo scopo, ma includono anche i vantaggi per gli abbonati, incluso l'uso di Windows e di altri software Microsoft per l'installazione e l'esecuzione per lo sviluppo e il test, un credito singolo mensile di Azure DevTest da usare per la sperimentazione dei servizi di Azure e l'esecuzione di attività di sviluppo e test nel cloud, formazione, supporto e molto altro.
[Confrontare vantaggi e prezzi delle sottoscrizioni cloud](https://visualstudio.microsoft.com/vs/pricing/)

### <a name="q-do-i-get-new-versions-of-visual-studio-if-i-buy-a-visual-studio-cloud-subscription"></a>D: si ottengono le nuove versioni di Visual Studio acquistando una sottoscrizione cloud di Visual Studio?
R: sì. Non appena vengono rilasciate nuove versioni, è possibile scaricarle ed eseguirle. È anche possibile continuare a eseguire le versioni precedenti.

### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-from-my-software-reseller"></a>D: è possibile acquistare sottoscrizioni cloud di Visual Studio da un rivenditore di software?
R: Sì, è possibile, se il rivenditore partecipa al programma Cloud Solution Provider (CSP). Chiedere semplicemente.

## <a name="related-resources"></a>Risorse correlate
- [Portale di amministrazione delle sottoscrizioni di Visual Studio](https://manage.visualstudio.com/)
- [Supporto per la sottoscrizione di Visual Studio](https://visualstudio.microsoft.com/vs/support/)
- [Acquisto di sottoscrizioni cloud di Visual Studio per i CSP](vscloud-csp.md)

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Acquistare subito sottoscrizioni cloud
- [Visual Studio Professional mensili](https://marketplace.visualstudio.com/items?itemName=ms.vs-professional-monthly)
- [Visual Studio Enterprise mensili](https://marketplace.visualstudio.com/items?itemName=ms.vs-enterprise-monthly)
