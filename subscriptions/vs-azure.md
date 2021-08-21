---
title: Microsoft Azure vantaggio nelle sottoscrizioni Visual Studio | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 08/20/2021
ms.topic: how-to
description: Informazioni su come attivare il vantaggio di credito singolo Azure DevTest incluso nella sottoscrizione Visual Studio sottoscrizione.
ms.openlocfilehash: a783d0b95c8b64474e19bfae412378c17583a633
ms.sourcegitcommit: bb1487ef906875ee83f2dc8567bd0bad823d727b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2021
ms.locfileid: "122621768"
---
# <a name="use-microsoft-azure-in-visual-studio-subscriptions"></a>Usare Microsoft Azure nelle sottoscrizioni di Visual Studio
I sottoscrittori di Visual Studio possono usare Microsoft Azure senza costi aggiuntivi.  Con il [credito individuale Azure DevTest mensile,](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)Azure è la sandbox personale per lo sviluppo/test.  È possibile effettuare il provisioning di macchine virtuali, servizi cloud e altre risorse di Azure.  L'importo del credito varia in base al livello della sottoscrizione.

## <a name="activation-steps"></a>Passaggi di attivazione
1. Accedere a [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2. Individuare il riquadro di Azure nella sezione Strumenti della pagina Vantaggi e selezionare **il collegamento** Attiva nella parte inferiore del riquadro del vantaggio.
   > [!div class="mx-imgBorder"]
   > ![Riquadro Azure](_img/vs-azure/vs-azure-tile.png "Fare clic sul pulsante &quot;Attiva&quot; nel riquadro di Azure per iniziare.")

3. Se non si ha una sottoscrizione di Azure esistente, verrà chiesto di immettere le informazioni necessarie per creare la sottoscrizione di Azure.  Il primo passaggio consiste nel fornire le informazioni personali e quindi selezionare **Avanti.**
   > [!div class="mx-imgBorder"]
   > ![Registrazione di Azure](_img/vs-azure/vs-azure-about-you.png "Aggiungere le informazioni di contatto personali alla sottoscrizione di Azure.")

4. Successivamente, è necessario verificare l'identità usando un semplice codice di verifica. Specificare il numero di telefono e scegliere se si desidera ricevere il codice tramite SMS o telefono.  Immettere il codice ricevuto e selezionare **Verifica codice**.   
   > [!div class="mx-imgBorder"]
   > ![Preparazione di Azure](_img/vs-azure/vs-azure-identity.png "Richiedere un codice di verifica e quindi immetterlo per continuare.")

5. Per il passaggio finale, selezionare la casella di controllo per accettare le condizioni e quindi selezionare **Iscrizione.**  Questo è tutto ciò che occorre fare.
   > [!div class="mx-imgBorder"]
   > ![Iscrizione ad Azure](_img/vs-azure/vs-azure-agreement.png "Fare clic sul pulsante &quot;Iscrizione&quot; per completare la creazione della sottoscrizione di Azure.")

0. Il centro di avvio rapido del dashboard di Azure viene caricato.  
   > [!div class="mx-imgBorder"]
   > ![Dashboard di Azure](_img/vs-azure/vs-azure-quick-start.png "Dopo aver creato la sottoscrizione di Azure, si verrà reindirizzati al portale di Azure.") 

0. Aggiungere un [segnalibro portale di Azure](https://portal.azure.com) per un facile accesso in futuro.

## <a name="maintain-a-subscription-to-use-monthly-credits"></a>Gestire una sottoscrizione per usare crediti mensili
Se la sottoscrizione Visual Studio scade o viene rimossa, tutti i vantaggi della sottoscrizione, incluso il credito singolo mensile di Azure per sviluppo/test non sono più disponibili. Per continuare a usare Azure con un credito mensile, è necessario rinnovare la sottoscrizione, acquistare una nuova sottoscrizione e/o trasferire le risorse di Azure in un'altra sottoscrizione di Azure che include il credito individuale di sviluppo/test di Azure.  

> [!IMPORTANT]
> È necessario trasferire le risorse in un'altra sottoscrizione di Azure prima che la sottoscrizione di Azure corrente sia disabilitata oppure si perderà l'accesso ai dati.  

Esistono diversi modi per continuare a usare un credito mensile per Azure.  Per salvare le risorse di Azure, è necessario [trasferire](/azure/azure-resource-manager/management/move-resource-group-and-subscription) le risorse in un'altra sottoscrizione di Azure, indipendentemente dall'azione scelta di seguito. 

- **Se si acquista direttamente la Visual Studio,** acquistare una nuova sottoscrizione o rinnovarla tramite Microsoft Store.  
    - [Visual Studio Enterprise](https://www.microsoft.com/p/visual-studio-enterprise-subscription/dg7gmgf0dst4?activetab=pivot%3aoverviewtab)
    - [Visual Studio Professional](https://www.microsoft.com/p/visual-studio-professional-subscription/dg7gmgf0dst3?activetab=pivot%3aoverviewtab)
    - [Visual Studio Test Professional](https://www.microsoft.com/p/visual-studio-test-professional-subscription/dg7gmgf0dst6?activetab=pivot%3aoverviewtab)
- **Se un utente dell'organizzazione** acquista sottoscrizioni per l'organizzazione, contattare l'amministratore della sottoscrizione [Visual Studio](./contact-my-admin.md) e richiedere una sottoscrizione che fornisce il credito mensile necessario.  
- **Se si ha un'altra sottoscrizione Visual Studio** allo stesso livello di sottoscrizione, è possibile usarla per configurare una nuova sottoscrizione di credito di Azure.  

Usare la tabella Eligibility riportata di seguito per determinare il numero di crediti inclusi in ogni tipo di sottoscrizione.  


## <a name="convert-your-azure-subscription-to-pay-as-you-go"></a>Convertire la sottoscrizione di Azure in pagamento in base al go

Se non è più necessaria una sottoscrizione o un credito Visual Studio ma si vogliono continuare a usare le risorse di [Azure,](/azure/azure-resource-manager/management/move-resource-group-and-subscription) trasferire le risorse in un'altra sottoscrizione di Azure o convertire la sottoscrizione di Azure in prezzi con pagamento in base al consumo rimuovendo il limite di spesa [.](/azure/cost-management-billing/manage/spending-limit#remove-the-spending-limit-in-azure-portal) 

Se non si intraprendere una di queste azioni, la sottoscrizione di Azure verrà disabilitata al momento specificato nella notifica di posta elettronica.  Se la sottoscrizione è disabilitata, è possibile riabilitarla come sottoscrizione con pagamento in base al pagamento seguendo [questa procedura.](https://docs.microsoft.com/azure/cost-management-billing/manage/switch-azure-offer)

## <a name="have-a-question"></a>Hai una domanda?
In caso di domande sul trasferimento di risorse, sulla rimozione [](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) dei limiti di spesa o su altri argomenti di Azure, è possibile inviare una richiesta di supporto tecnico di Azure nel portale di Azure. 

## <a name="eligibility"></a>Idoneità
|                 Livello di sottoscrizione/Programma                 |           Vantaggi           |                         Rinnovabile?                          |
|--------------------------------------------------------------|-----------------------------|-------------------------------------------------------------|
|              Visual Studio Enterprise Standard               |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|              Visual Studio Enterprise sottoscrizione con GitHub Enterprise               |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|               Visual Studio Enterprise (mensile)               |        Non disponibile        |                                                             |
|             Visual Studio Professional Standard              |     Credito mensile pari a 50 dollari USA      |                             Sì
|              Visual Studio Professional sottoscrizione con GitHub Enterprise              |     Credito mensile pari a 50 dollari USA     |                             Sì                             |
|              Visual Studio Professional (mensile)              |        Non disponibile        |                                                             |
|                    Visual Studio Test Pro                    |     Credito mensile pari a 50 dollari USA      |                             Sì                             |
|                        MSDN Platforms                        |     Credito mensile pari a 100 dollari USA     |                             Sì                             |
|               Visual Studio Enterprise - NFR<sup>1</sup>                 |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|                Visual Studio Enterprise - FTE                |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|     Visual Studio Enterprise - Microsoft Partner Network     |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|    Visual Studio Professional - Microsoft Partner Network    |        Non disponibile        |                                                             |
|        Visual Studio Enterprise - Imagine (Standard)         |        Non disponibile        |                                                             |
|         Visual Studio Enterprise - Imagine (Premium)         |        Non disponibile        |                                                             |
|             Visual Studio Enterprise - BizSpark              |     Credito mensile pari a 150 dollari USA     |                             Sì                             |
|      Visual Studio Enterprise – MCT Software & Services      |     Credito mensile pari a 100 dollari USA     |                             Sì                             |
| Visual Studio Enterprise - MCT Developer Software & Services |     Credito mensile pari a 150 dollari USA     |                             Sì                             |

<sup>1</sup>*Include: Not for Resale (NFR), Most Valuable Professional (MVP), Regional Director (RD), Visual Studio Industry Partner (VSIP) Excludes: NFR Basic*  

> [!NOTE]
> Microsoft non offre più sottoscrizioni annuali di Visual Studio Professional e Visual Studio Enterprise nelle sottoscrizioni cloud. Non verrà apportata alcuna modifica all'esperienza dei clienti corrente, né alle possibilità di rinnovo, espansione, riduzione o annullamento delle sottoscrizioni esistenti. I nuovi clienti sono invitati a esplorare [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) diverse opzioni per acquistare Visual Studio.

Non si è certi della sottoscrizione in uso?  Connessione visualizzare [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) tutte le sottoscrizioni assegnate all'indirizzo di posta elettronica. Se non sono visualizzate tutte le sottoscrizioni, è possibile che una o più sottoscrizioni siano assegnate a un indirizzo di posta elettronica diverso.  È necessario accedere con tale indirizzo di posta elettronica per visualizzare le sottoscrizioni.

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-do-i-submit-a-technical-support-incident-from-within-the-azure-portal"></a>D: come è possibile inviare una richiesta di supporto tecnico dal portale di Azure?
R: l'invio di una richiesta di supporto dal portale di Azure è un processo in tre fasi.
1. Attivare il vantaggio di supporto tecnico e ottenere l'ID di accesso dell'ID di contratto.
2. Collegare il contratto di supporto alla sottoscrizione di Azure.
3. Inviare una richiesta di supporto online.

Vedere la documentazione del [supporto tecnico](vs-tech-support.md) per informazioni dettagliate.

### <a name="q-who-owns-the-intellectual-property-i-create-using-my-azure-devtest-individual-credit"></a>D: Who è proprietaria della proprietà intellettuale creata usando il credito individuale Azure DevTest?
A: La proprietà intellettuale prodotta da un dipendente creato in base alle risorse fornite dall'azienda è quindi la proprietà intellettuale dell'azienda che fornisce la risorsa. Pertanto, se si riceve la sottoscrizione Visual Studio tramite il datore di lavoro, si applicano i criteri di proprietà intellettuale. 

### <a name="q-how-can-i-find-out-what-my-azure-credit-balance-is"></a>D: Come è possibile scoprire qual è il saldo del credito Azure?
A: Per monitorare il saldo e ottenere altre informazioni utili sui crediti Azure, vedere Tenere traccia del saldo Contratto del cliente Microsoft [credito Azure.](https://docs.microsoft.com/azure/cost-management-billing/manage/mca-check-azure-credits-balance?tabs=portal)

## <a name="support-resources"></a>Risorse di supporto
- Serve aiuto con Azure?  vedere le risorse seguenti:
  - Supporto tecnico: [https://azure.microsoft.com/support/options/](https://azure.microsoft.com/support/options/)
  - [Azure Suggerimenti & Tricks](https://microsoft.github.io/AzureTipsAndTricks/ "Azure Suggerimenti & Tricks") 
- Per assistenza su vendite, sottoscrizioni, account e fatturazione per Sottoscrizioni di Visual Studio, contattare il supporto Visual Studio [sottoscrizioni.](https://aka.ms/vssubscriberhelp)
- Per domande sull'IDE di Visual Studio, Azure DevOps Services o altri prodotti e servizi Visual Studio,  Visitare [Visual Studio Supporto tecnico](https://visualstudio.microsoft.com/support/).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sugli strumenti e i servizi Microsoft, consultare la documentazione di:
- [Azure](/azure/)
- [Azure DevOps](/azure/devops/)
- [IDE di Visual Studio](/visualstudio/)