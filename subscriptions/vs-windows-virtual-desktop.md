---
title: Microsoft Windows Virtual Desktop in Visual Studio sottoscrizioni | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 03/17/2021
ms.topic: conceptual
description: Informazioni su come sfruttare i vantaggi di Desktop Windows Microsoft tramite la sottoscrizione Visual Studio
ms.openlocfilehash: aa5a9a251e7f70900e49be75ce785a5c6f318c42d5330a9bc4e7f91078e91310
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121364203"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Accedere Windows Desktop virtuale nelle sottoscrizioni 
Visual Studio sottoscrittori possono ora usare i crediti individuali di sviluppo/test di Azure per i servizi desktop Windows Microsoft.  
Windows Desktop virtuale è un servizio desktop e di virtualizzazione delle app completo in esecuzione nel cloud. È l'unica infrastruttura VDI (Virtual Desktop Infrastructure) che offre gestione semplificata, Windows 10 multi-sessione, ottimizzazioni per Microsoft 365 Apps for enterprise e supporto per gli ambienti Servizi Desktop remoto (Servizi Desktop remoto). Distribuire e ridimensionare Windows desktop e app in Azure in pochi minuti e ottenere funzionalità di sicurezza e conformità predefinite.
Ecco cosa si può fare quando si esegue Desktop virtuale Windows in Azure:
- Configurare una distribuzione di Windows 10 multisessione che offre una versione completa Windows 10 con scalabilità
- Virtualizzare Microsoft 365 Apps for enterprise e ottimizzarlo per l'esecuzione in scenari virtuali multiutente
- Fornire ai desktop virtuali di Windows 7 aggiornamenti della sicurezza estesi gratuiti
- Portare i desktop e le app esistenti di Servizi Desktop remoto e Windows Server in qualsiasi computer
- Virtualizzare sia i desktop che le app
- Gestire Windows 10 desktop e app Windows Server e Windows 7 con un'esperienza di gestione unificata. Per altre informazioni sulle attività che è possibile eseguire con Desktop virtuale Windows, guardare il [video introduttivo](/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Usare Windows Desktop virtuale con Azure 
Visual Studio sottoscrittori hanno ora diversi modi per usare le sottoscrizioni di Azure per pagare Windows servizi Desktop virtuale:
- Crediti individuali di [Azure DevTest.](vs-azure.md)  I sottoscrittori che ricevono crediti individuali di Azure DevTest come parte delle sottoscrizioni possono usare tali crediti per pagare Windows servizi Desktop virtuale.  L'importo del credito mensile dipende dal livello di sottoscrizione.
- [Sottoscrizioni di Azure DevTest con pagamento in base al prezzo.](vs-azure-payg.md)  È possibile creare sottoscrizioni di Azure e collegare uno strumento di pagamento per avere un modo semplice per pagare l Windows'utilizzo di Desktop virtuale. 
- [Offerta Azure Enterprise Agreement DevTest](azure-ea-devtest.md).  Con questa offerta, i sottoscrittori con Enterprise possono pagare per Windows desktop virtuale con Azure a prezzi scontati. 

## <a name="requirements"></a>Requisiti
Windows Desktop virtuale richiede un Azure Active Directory (Azure AD) a cui verranno unite le macchine virtuali.  Gli utenti devono essere membri di questa Azure AD.  Sono disponibili due opzioni per implementare il Azure AD:
- Azure AD Directory Services.  Per la maggior parte degli utenti, questa è l'opzione più semplice da implementare.
- Una macchina virtuale che esegue un modello di controller di dominio.  Questa opzione richiede più lavoro per la configurazione, ma offre alla maggior parte degli utenti un costo operativo inferiore.
Per visualizzare un elenco completo dei prerequisiti per l'uso Windows Desktop virtuale, visitare la Windows panoramica di Desktop [virtuale](/azure/virtual-desktop/overview#requirements). 

## <a name="get-started"></a>Introduzione 
Quando tutti i prerequisiti sono soddisfatti, è necessario completare diverse azioni per mettere in atto l'implementazione.  Per iniziare, vedere queste esercitazioni:
- [Creare un tenant di Desktop virtuale Windows](/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- [Creare un pool di host](/azure/virtual-desktop/create-host-pools-azure-marketplace) usando il portale di Azure
- [Gestire i gruppi di app](/azure/virtual-desktop/manage-app-groups) Windows Desktop virtuale

## <a name="eligibility"></a>Idoneità
| Livello di sottoscrizione                                                 |     Canali                                            | Vantaggi                                                          | Rinnovabile?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, Retail, | Disponibile|  Sì          |
| Visual Studio Enterprise sottoscrizione con GitHub Enterprise  | Vl | Disponibile|  Sì          |
| Visual Studio Professional (Standard) | VL, Azure, Retail                                       | Disponibile                                                             |  Sì             |
| Visual Studio Professional sottoscrizione con GitHub Enterprise | Vl                                       | Disponibile                                        |  Sì           |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Disponibile|  Sì          |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Disponibile                                         |  Sì          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Non disponibile  | N/A |
| Visual Studio Enterprise, Visual Studio Professional (cloud mensile) | Azure | Non disponibile | N/A |

<sup>1</sup>*Include: Not for Resale (NFR), FTE, Most Valuable Professional (MVP), Regional Director (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine, NFR Basic*  

> [!NOTE]
> Microsoft non offre più sottoscrizioni annuali di Visual Studio Professional e Visual Studio Enterprise nelle sottoscrizioni cloud. Non verrà apportata alcuna modifica all'esperienza dei clienti corrente, né alle possibilità di rinnovo, espansione, riduzione o annullamento delle sottoscrizioni esistenti. I nuovi clienti sono invitati a passare [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) a per esplorare diverse opzioni per l'acquisto Visual Studio.

Non si è certi della sottoscrizione in uso?  Connessione a per [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) visualizzare tutte le sottoscrizioni assegnate all'indirizzo di posta elettronica. Se non sono visualizzate tutte le sottoscrizioni, è possibile che una o più sottoscrizioni siano assegnate a un indirizzo di posta elettronica diverso.  È necessario accedere con tale indirizzo di posta elettronica per visualizzare le sottoscrizioni.

## <a name="see-also"></a>Vedi anche
- [Documentazione di Azure](/azure/)
- [Documentazione di Desktop virtuale Windows](/azure/virtual-desktop/)
- [Visual Studio sottoscrizioni](https://my.visualstudio.com/gethelp)

## <a name="next-steps"></a>Passaggi successivi
-   Se è necessario acquistare sottoscrizioni Visual Studio, vedere:
     - [Prezzi per gli acquisti al dettaglio](https://visualstudio.microsoft.com/vs/pricing/) tramite il Microsoft Store
     - [Programmi per contratti multilicenza](https://www.microsoft.com/licensing/default)
-   Informazioni su [Windows Desktop virtuale](/azure/virtual-desktop/overview)