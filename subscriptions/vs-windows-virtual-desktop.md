---
title: Desktop virtuale Microsoft Windows nelle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 09/08/2020
ms.topic: conceptual
description: Scopri come sfruttare i vantaggi del desktop virtuale Microsoft Windows tramite la sottoscrizione di Visual Studio
ms.openlocfilehash: f598aca8d277ca443b10dac289fae756ccd95432
ms.sourcegitcommit: f8d14fab194fcb30658f23f700da07d35ffc9d4a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2020
ms.locfileid: "89561364"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Accedere al desktop virtuale Windows nelle sottoscrizioni 
I sottoscrittori di Visual Studio sono ora in grado di usare i singoli crediti di sviluppo/test di Azure per i servizi desktop virtuali di Microsoft Windows.  
Desktop virtuale di Windows è un servizio di virtualizzazione desktop e app completo in esecuzione nel cloud. Si tratta dell'unica infrastruttura VDI (Virtual Desktop Infrastructure) che offre funzionalità di gestione semplificata, Windows 10 multisessione, ottimizzazioni per Microsoft 365 app per le aziende e supporto per gli ambienti Servizi Desktop remoto (RDS). Distribuisci e ridimensiona le tue app e i tuoi desktop Windows in Azure in pochi minuti e Ottieni funzionalità predefinite di sicurezza e conformità.
Ecco cosa si può fare quando si esegue Desktop virtuale Windows in Azure:
- Configurare una distribuzione di Windows 10 multisessione che offre una versione completa Windows 10 con scalabilità
- Virtualizzare Microsoft 365 Apps for enterprise e ottimizzarlo per l'esecuzione in scenari virtuali multiutente
- Fornire ai desktop virtuali di Windows 7 aggiornamenti della sicurezza estesi gratuiti
- Portare i desktop e le app esistenti di Servizi Desktop remoto e Windows Server in qualsiasi computer
- Virtualizzare sia i desktop che le app
- Consente di gestire i desktop e le app Windows 10, Windows Server e Windows 7 con un'esperienza di gestione unificata per ulteriori informazioni sulle operazioni che è possibile eseguire con il desktop virtuale di Windows, guardare il [video introduttivo](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Usare desktop virtuale di Windows con Azure 
I sottoscrittori di Visual Studio ora hanno diversi modi per usare le sottoscrizioni di Azure per pagare i servizi desktop virtuali Windows:
- [Azure DevTest i singoli crediti](vs-azure.md).  Gli abbonati che ricevono Azure DevTest i singoli crediti come parte delle sottoscrizioni possono usare tali crediti per pagare i servizi desktop virtuali Windows.  La quantità di credito mensile dipende dal livello di abbonamento.
- [Sottoscrizioni con pagamento in base al consumo di Azure DevTest](vs-azure-payg.md).  Puoi creare sottoscrizioni di Azure e alleghi uno strumento di pagamento per ottenere un modo semplice per pagare l'utilizzo di desktop virtuali Windows. 
- [Offerta Azure Enterprise Agreement DevTest](azure-ea-devtest.md).  Con questa offerta, gli abbonati con contratti Enterprise possono pagare per desktop virtuale Windows con Azure a prezzi scontati. 

## <a name="requirements"></a>Requisiti
Per desktop virtuale Windows è necessario un Azure Active Directory (Azure AD) a cui verranno unite le macchine virtuali.  Gli utenti devono essere membri di questo Azure AD.  Sono disponibili due opzioni per implementare la Azure AD:
- Servizi directory Azure AD.  Per la maggior parte degli utenti, si tratta dell'opzione più semplice da implementare.
- Una macchina virtuale che esegue un controller di dominio promo.  Questa opzione richiede un maggior numero di operazioni di configurazione, ma offre alla maggior parte degli utenti un costo operativo più basso.
Per visualizzare un elenco completo dei prerequisiti per l'utilizzo di desktop virtuale di Windows, visitare la [pagina Panoramica](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)di desktop virtuali di Windows. 

## <a name="get-started"></a>Introduzione 
Quando tutti i prerequisiti sono soddisfatti, è necessario completare diverse azioni per implementare il proprio ambiente.  Per iniziare, vedere le esercitazioni seguenti:
- [Creare un tenant di Desktop virtuale Windows](https://docs.microsoft.com/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- [Creare un pool host](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace) usando il portale di Azure
- [Gestire i gruppi di app](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups) per desktop virtuale Windows

## <a name="eligibility"></a>Idoneità
| Livello di sottoscrizione                                                 |     Canali                                            | Vantaggi                                                          | Rinnovabile?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, Retail, | Disponibile|  Sì          |
| Visual Studio Enterprise con GitHub Enterprise  | VL | Disponibile|  Sì          |
| Visual Studio Professional (Standard) | VL, Azure, Retail                                       | Disponibile                                                             |  Sì             |
| Visual Studio Professional con GitHub Enterprise | VL                                       | Disponibile                                        |  Sì           |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Disponibile|  Sì          |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Disponibile                                         |  Sì          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Non disponibile  | N/D |
| Visual Studio Enterprise, Visual Studio Professional (cloud mensile) | Azure | Non disponibile | N/D |

<sup>1</sup>  *include: not for Resale (NFR), ETP, most VALUABLE Professional (MVP), Regional Director (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine*

> [!NOTE]
> Microsoft non offre più sottoscrizioni annuali di Visual Studio Professional e Visual Studio Enterprise nelle sottoscrizioni cloud. Non verrà apportata alcuna modifica all'esperienza dei clienti corrente, né alle possibilità di rinnovo, espansione, riduzione o annullamento delle sottoscrizioni esistenti. I nuovi clienti sono invitati a passare a [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) per esplorare diverse opzioni per l'acquisto di Visual Studio.

Non si è certi della sottoscrizione in uso?  Connettersi a per [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) visualizzare tutte le sottoscrizioni assegnate all'indirizzo di posta elettronica. Se non sono visualizzate tutte le sottoscrizioni, è possibile che una o più sottoscrizioni siano assegnate a un indirizzo di posta elettronica diverso.  È necessario accedere con tale indirizzo di posta elettronica per visualizzare le sottoscrizioni.

## <a name="see-also"></a>Vedere anche
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Desktop virtuale Windows](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Passaggi successivi
-   Se è necessario acquistare sottoscrizioni di Visual Studio, vedere:
     - [Prezzi per gli acquisti al dettaglio](https://visualstudio.microsoft.com/vs/pricing/) tramite il Microsoft Store
     - [Programmi per contratti multilicenza](https://www.microsoft.com/licensing/default)
-   Informazioni sul [desktop virtuale Windows](https://docs.microsoft.com/azure/virtual-desktop/overview) 
