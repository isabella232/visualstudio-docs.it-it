---
title: Microsoft Windows Virtual Desktop in Visual Studio sottoscrizioni | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 03/17/2021
ms.topic: conceptual
description: Informazioni su come sfruttare i vantaggi di Microsoft Windows Virtual Desktop tramite la sottoscrizione Visual Studio
ms.openlocfilehash: 926eb94e140fda630439083c39d733c3ff366886
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128375644"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Accedere Windows Desktop virtuale nelle sottoscrizioni 
Visual Studio i sottoscrittori possono ora usare i crediti individuali di sviluppo/test di Azure per i servizi Desktop virtuale Windows Microsoft.  
Windows Desktop virtuale è un servizio completo di virtualizzazione di desktop e app in esecuzione nel cloud. È l'unica infrastruttura di desktop virtuale (VDI) che offre gestione semplificata, Windows 10 multi-sessione, ottimizzazioni per Microsoft 365 Apps for enterprise e supporto per gli ambienti Servizi Desktop remoto (RDS). Distribuire e ridimensionare Windows desktop e app in Azure in pochi minuti e ottenere funzionalità di sicurezza e conformità predefinite.
Ecco cosa si può fare quando si esegue Desktop virtuale Windows in Azure:
- Configurare una distribuzione di Windows 10 multisessione che offre una versione completa Windows 10 con scalabilità
- Virtualizzare Microsoft 365 Apps for enterprise e ottimizzarlo per l'esecuzione in scenari virtuali multiutente
- Fornire ai desktop virtuali di Windows 7 aggiornamenti della sicurezza estesi gratuiti
- Portare i desktop e le app esistenti di Servizi Desktop remoto e Windows Server in qualsiasi computer
- Virtualizzare sia i desktop che le app
- Gestire Windows 10, Windows Server e Windows 7 desktop e app con un'esperienza di gestione unificata Per altre informazioni sulle funzionalità di Windows Virtual Desktop, guardare il [video introduttivo](/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Usare Windows desktop virtuale con Azure 
Visual Studio i sottoscrittori hanno ora diversi modi per usare le sottoscrizioni di Azure per pagare Windows servizi Desktop virtuale:
- [Crediti singoli di Azure DevTest.](vs-azure.md)  I sottoscrittori che ricevono crediti individuali di Azure DevTest come parte delle sottoscrizioni possono usare tali crediti per pagare Windows servizi Di Desktop virtuale.  L'importo del credito mensile dipende dal livello di sottoscrizione.
- Sottoscrizioni con pagamento in base al go di [Azure DevTest.](vs-azure-payg.md)  È possibile creare sottoscrizioni di Azure e collegare uno strumento di pagamento per avere un modo semplice per pagare l'Windows di Desktop virtuale. 
- [Offerta DevTest di Azure Enterprise Agreement.](azure-ea-devtest.md)  Con questa offerta, i sottoscrittori con Enterprise possono pagare Windows Desktop virtuale con Azure a prezzi scontati. 

## <a name="requirements"></a>Requisiti
Windows Desktop virtuale richiede un Azure Active Directory (Azure AD) a cui verranno unite le macchine virtuali.  Gli utenti devono essere membri di questa Azure AD.  Esistono due opzioni per implementare il Azure AD:
- Azure AD servizi directory.  Per la maggior parte degli utenti, questa è l'opzione più semplice da implementare.
- Una macchina virtuale che esegue un modello di controller di dominio.  Questa opzione richiede più lavoro per la configurazione, ma offre alla maggior parte degli utenti un costo operativo inferiore.
Per visualizzare un elenco completo dei prerequisiti per l'Windows desktop virtuale, visitare la pagina Windows panoramica di Desktop [virtuale](/azure/virtual-desktop/overview#requirements). 

## <a name="get-started"></a>Introduzione 
Quando tutti i prerequisiti sono soddisfatti, è necessario completare diverse azioni per ottenere l'implementazione.  Per iniziare, vedere queste esercitazioni:
- [Creare un tenant di Desktop virtuale Windows](/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- [Creare un pool di host](/azure/virtual-desktop/create-host-pools-azure-marketplace) usando il portale di Azure
- [Gestire i gruppi di app](/azure/virtual-desktop/manage-app-groups) Windows Desktop virtuale

## <a name="eligibility"></a>Idoneità
| Livello di sottoscrizione                                                 |     Canali                                            | Vantaggi                                                          | Rinnovabile?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, Retail, | Disponibile|  Sì          |
| Visual Studio Enterprise sottoscrizione con GitHub Enterprise  | VL | Disponibile|  Sì          |
| Visual Studio Professional (Standard) | VL, Azure, Retail                                       | Disponibile                                                             |  Sì             |
| Visual Studio Professional sottoscrizione con GitHub Enterprise | VL                                       | Disponibile                                        |  Sì           |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Disponibile|  Sì          |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Disponibile                                         |  Sì          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Non disponibile  | N/A |
| Visual Studio Enterprise, Visual Studio Professional (cloud mensile) | Azure | Non disponibile | N/A |

<sup>1</sup>*Include: Not for Resale (NFR), FTE, Most Valuable Professional (MVP), Regional Director (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine, NFR Basic*  

> [!NOTE]
> Microsoft non offre più sottoscrizioni annuali di Visual Studio Professional e Visual Studio Enterprise nelle sottoscrizioni cloud. Non verrà apportata alcuna modifica all'esperienza dei clienti corrente, né alle possibilità di rinnovo, espansione, riduzione o annullamento delle sottoscrizioni esistenti. I nuovi clienti sono invitati a esplorare [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) diverse opzioni per l'acquisto di Visual Studio.

Non si è certi della sottoscrizione in uso?  Connessione visualizzare [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) tutte le sottoscrizioni assegnate all'indirizzo di posta elettronica. Se non sono visualizzate tutte le sottoscrizioni, è possibile che una o più sottoscrizioni siano assegnate a un indirizzo di posta elettronica diverso.  È necessario accedere con tale indirizzo di posta elettronica per visualizzare le sottoscrizioni.

## <a name="see-also"></a>Vedi anche
- [Documentazione di Azure](/azure/)
- [Documentazione di Desktop virtuale Windows](/azure/virtual-desktop/)
- [Visual Studio sottoscrizioni](https://my.visualstudio.com/gethelp)

## <a name="next-steps"></a>Passaggi successivi
-   Se è necessario acquistare Visual Studio sottoscrizioni, vedere:
     - [Prezzi per gli acquisti al dettaglio](https://visualstudio.microsoft.com/vs/pricing/) tramite il Microsoft Store
     - [Programmi per contratti multilicenza](https://www.microsoft.com/licensing/default)
-   Informazioni su [Windows Desktop virtuale](/azure/virtual-desktop/overview)