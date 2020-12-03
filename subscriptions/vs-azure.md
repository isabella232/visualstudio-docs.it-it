---
title: Microsoft Azure vantaggio nelle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 10/28/2020
ms.topic: how-to
description: Informazioni su come attivare il vantaggio di credito singolo di Azure DevTest incluso nella sottoscrizione di Visual Studio.
ms.openlocfilehash: bfd94ef7995ed5f456462e1bce6aa0d4d045bdd0
ms.sourcegitcommit: 29099741fcf94a5aef2655ee16605728b8b9a0ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96538007"
---
# <a name="use-microsoft-azure-in-visual-studio-subscriptions"></a>Usare Microsoft Azure nelle sottoscrizioni di Visual Studio
I sottoscrittori di Visual Studio possono usare Microsoft Azure senza costi aggiuntivi.  Con il tuo [credito mensile Azure DevTest individual](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/), Azure è la tua sandbox personale per sviluppo/test.  È possibile effettuare il provisioning di macchine virtuali, servizi cloud e altre risorse di Azure.  L'importo del credito varia in base al livello della sottoscrizione.

## <a name="activation-steps"></a>Passaggi di attivazione
1. Accedere a [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2. Individuare il riquadro Azure nella sezione strumenti della pagina vantaggi e selezionare **attiva** collegamento nella parte inferiore del riquadro del vantaggio.
   > [!div class="mx-imgBorder"]
   > ![Riquadro Azure](_img/vs-azure/vs-azure-tile.png "Per iniziare, fare clic sul pulsante ' attiva ' nel riquadro di Azure.")

3. Se non si ha una sottoscrizione di Azure esistente, verrà richiesto di immettere le informazioni necessarie per creare la sottoscrizione di Azure.  Il primo passaggio consiste nel fornire le informazioni personali e quindi selezionare **Avanti**.
   > [!div class="mx-imgBorder"]
   > ![Registrazione di Azure](_img/vs-azure/vs-azure-about-you.png "Aggiungere le informazioni di contatto personali alla sottoscrizione di Azure.")

4. Successivamente, sarà necessario verificare l'identità usando un semplice codice di verifica. Specificare il numero di telefono e scegliere se si desidera ricevere il codice in base a testo o telefono.  Immettere il codice ricevuto e selezionare **Verifica codice**.   
   > [!div class="mx-imgBorder"]
   > ![Preparazione di Azure](_img/vs-azure/vs-azure-identity.png "Richiedere un codice di verifica e quindi immetterlo per continuare.")

5. Per il passaggio finale, selezionare la casella di controllo per accettare le condizioni e quindi selezionare **Iscriviti**.  Questo è tutto ciò che occorre fare.
   > [!div class="mx-imgBorder"]
   > ![Iscrizione ad Azure](_img/vs-azure/vs-azure-agreement.png "Fare clic sul pulsante "Iscriviti" per completare la creazione della sottoscrizione di Azure.")

0. Il centro di avvio rapido del dashboard di Azure viene caricato.  
   > [!div class="mx-imgBorder"]
   > ![Dashboard di Azure](_img/vs-azure/vs-azure-quick-start.png "Dopo la creazione della sottoscrizione di Azure, si verrà reindirizzati al portale di Azure.") 

0. Aggiungere un segnalibro al [portale di Azure](https://portal.azure.com) per facilitarne l'accesso in futuro.

## <a name="maintain-a-subscription-to-use-monthly-credits"></a>Gestione di una sottoscrizione per l'utilizzo di crediti mensili
Se la sottoscrizione di Visual Studio scade o viene rimossa, tutti i vantaggi della sottoscrizione, incluso il credito mensile per sviluppo/test di Azure, non sono più disponibili. Per continuare a usare Azure con un credito mensile, è necessario rinnovare la sottoscrizione, acquistare una nuova sottoscrizione o trasferire il vantaggio di Azure a una sottoscrizione attiva che includa il credito individuale per sviluppo/test di Azure.  

> [!IMPORTANT]
> È necessario trasferire le risorse a un'altra sottoscrizione di Azure prima che la sottoscrizione di Azure corrente venga disabilitata o si perderà l'accesso ai dati.  

Esistono diversi modi per continuare a usare un credito mensile per Azure.  Per salvare le risorse di Azure, sarà necessario [trasferire le risorse](/azure/azure-resource-manager/management/move-resource-group-and-subscription) a un'altra sottoscrizione di Azure, indipendentemente dall'azione scelta di seguito. 

- **Se acquisti direttamente la sottoscrizione di Visual Studio**, Acquista una nuova sottoscrizione o rinnova la sottoscrizione tramite Microsoft Store.  
    - [Visual Studio Enterprise](https://www.microsoft.com/p/visual-studio-enterprise-subscription/dg7gmgf0dst4?activetab=pivot%3aoverviewtab)
    - [Visual Studio Professional](https://www.microsoft.com/p/visual-studio-professional-subscription/dg7gmgf0dst3?activetab=pivot%3aoverviewtab)
    - [Visual Studio Test Professional](https://www.microsoft.com/p/visual-studio-test-professional-subscription/dg7gmgf0dst6?activetab=pivot%3aoverviewtab)
- **Se un utente dell'organizzazione acquista sottoscrizioni per l'organizzazione**, [contattare l'amministratore della sottoscrizione di Visual Studio](./contact-my-admin.md) e richiedere una sottoscrizione che fornisca il credito mensile necessario.  
- **Se si ha un'altra sottoscrizione di Visual Studio attiva** allo stesso livello di sottoscrizione associata a un altro account Microsoft, è possibile trasferire il vantaggio di Azure a un'altra sottoscrizione attiva di Visual Studio [aggiungendo un account alternativo](./manage-vs-subscriptions.md#managing-my-profile) nel [portale delle sottoscrizioni](https://my.visualstudio.com/subscriptions)di Visual Studio.  

Usare la tabella di idoneità riportata di seguito per determinare il numero di crediti inclusi in ogni tipo di sottoscrizione.  


## <a name="convert-your-azure-subscription-to-pay-as-you-go"></a>Converti la tua sottoscrizione di Azure in un modello con pagamento in base al consumo

Se non è più necessario un credito o una sottoscrizione di Visual Studio, ma si vuole continuare a usare le risorse di Azure, [trasferire le risorse](/azure/azure-resource-manager/management/move-resource-group-and-subscription) in un'altra sottoscrizione di Azure o convertire la sottoscrizione di Azure in prezzi con pagamento in base al [consumo rimuovendo il limite di spesa](/azure/cost-management-billing/manage/spending-limit#remove-the-spending-limit-in-azure-portal). 

Se non si esegue una di queste azioni, la sottoscrizione di Azure verrà disabilitata ed eliminata 30 giorni dopo la ricezione della notifica tramite posta elettronica.  

## <a name="have-a-question"></a>Hai una domanda?
Per domande su come trasferire risorse, rimuovere i limiti di spesa o altri argomenti di Azure, è possibile [inviare una richiesta di supporto di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) nella portale di Azure. 

## <a name="eligibility"></a>Idoneità
|                 Livello di sottoscrizione/Programma                 |           Vantaggi           |                         Rinnovabile?                          |
|--------------------------------------------------------------|-----------------------------|-------------------------------------------------------------|
|              Visual Studio Enterprise Standard               |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|              Sottoscrizione di Visual Studio Enterprise con GitHub Enterprise               |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|               Visual Studio Enterprise (mensile)               |        Non disponibile        |                                                             |
|             Visual Studio Professional Standard              |     Credito mensile pari a 50 dollari USA      |                             Sì
|              Sottoscrizione di Visual Studio Professional con GitHub Enterprise              |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|              Visual Studio Professional (mensile)              |        Non disponibile        |                                                             |
|                    Visual Studio Test Pro                    |     Credito mensile pari a 50 dollari USA      |                             Sì                             |
|                        MSDN Platforms                        |     Credito mensile pari a 100 dollari USA     |                             Sì                             |
|               Visual Studio Enterprise - NFR\*               |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|                Visual Studio Enterprise - FTE                |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|     Visual Studio Enterprise - Microsoft Partner Network     |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|    Visual Studio Professional - Microsoft Partner Network    |        Non disponibile        |                                                             |
|        Visual Studio Enterprise - Imagine (Standard)         |        Non disponibile        |                                                             |
|         Visual Studio Enterprise - Imagine (Premium)         |        Non disponibile        |                                                             |
|             Visual Studio Enterprise - BizSpark              |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|      Visual Studio Enterprise – MCT Software & Services      |     Credito mensile pari a 100 dollari USA     |                             Sì                             |
| Visual Studio Enterprise - MCT Developer Software & Services |     Credito mensile pari a 150 dollari USA     |                             Sì                             |

*Include Not for Resale (NFR), Most Valuable Professional (MVP), Regional Director (RD), Visual Studio Industry Partner (VSIP)

> [!NOTE]
> Microsoft non offre più sottoscrizioni annuali di Visual Studio Professional e Visual Studio Enterprise nelle sottoscrizioni cloud. Non verrà apportata alcuna modifica all'esperienza dei clienti corrente, né alle possibilità di rinnovo, espansione, riduzione o annullamento delle sottoscrizioni esistenti. I nuovi clienti sono invitati a passare a [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) per esplorare diverse opzioni per l'acquisto di Visual Studio.

Non si è certi della sottoscrizione in uso?  Connettersi a per [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) visualizzare tutte le sottoscrizioni assegnate all'indirizzo di posta elettronica. Se non sono visualizzate tutte le sottoscrizioni, è possibile che una o più sottoscrizioni siano assegnate a un indirizzo di posta elettronica diverso.  È necessario accedere con tale indirizzo di posta elettronica per visualizzare le sottoscrizioni.

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-do-i-submit-a-technical-support-incident-from-within-the-azure-portal"></a>D: come è possibile inviare una richiesta di supporto tecnico dal portale di Azure?
R: l'invio di una richiesta di supporto dal portale di Azure è un processo in tre fasi.
1. Attivare il vantaggio di supporto tecnico e ottenere l'ID di accesso dell'ID di contratto.
2. Collegare il contratto di supporto alla sottoscrizione di Azure.
3. Inviare una richiesta di supporto online.

Vedere la documentazione del [supporto tecnico](vs-tech-support.md) per informazioni dettagliate.

### <a name="q-who-owns-the-intellectual-property-i-create-using-my-azure-devtest-individual-credit"></a>D: chi possiede la proprietà intellettuale che ho creato con il credito individuale Azure DevTest?
R: la proprietà intellettuale prodotta da un dipendente creato per le risorse fornite da tale società è quindi una proprietà intellettuale della società che fornisce la risorsa. Quindi, se si riceve la sottoscrizione di Visual Studio tramite il proprio datore di lavoro, si applicano i criteri di proprietà intellettuale. 

## <a name="support-resources"></a>Risorse di supporto
- Serve aiuto con Azure?  vedere le risorse seguenti:
  - Supporto tecnico: [https://azure.microsoft.com/support/options/](https://azure.microsoft.com/support/options/)
  - [Suggerimenti & per Azure](https://microsoft.github.io/AzureTipsAndTricks/ "Suggerimenti & per Azure") 
- Per assistenza in merito a vendite, sottoscrizioni, account e fatturazione per le sottoscrizioni di Visual Studio, contattare il [supporto delle sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/)di Visual Studio.
- Per domande sull'IDE di Visual Studio, Azure DevOps Services o altri prodotti e servizi Visual Studio,  Visita il [supporto tecnico di Visual Studio](https://visualstudio.microsoft.com/support/).

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sugli strumenti e i servizi Microsoft, consultare la documentazione di:
- [Azure](/azure/)
- [Azure DevOps](/azure/devops/)
- [IDE di Visual Studio](/visualstudio/)