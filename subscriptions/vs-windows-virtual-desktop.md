---
title: Vantaggi di Microsoft Windows Virtual Desktop nelle sottoscrizioni di Visual Studio Documenti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/01/2020
ms.topic: conceptual
description: Informazioni su come sfruttare i vantaggi di Microsoft Windows Virtual Desktop tramite la sottoscrizione di Visual Studio
ms.openlocfilehash: 3954a3e86c319b8d433e509a8b283201c3313410
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2020
ms.locfileid: "80550693"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Accedere a Windows Virtual Desktop nelle sottoscrizioni 
I sottoscrittori di Visual Studio sono ora in grado di usare i singoli crediti di sviluppo/test di Azure per i servizi Desktop virtuali di Microsoft Windows.Visual Studio subscribers are now able to use their Azure dev/test individual credits for Microsoft Windows Virtual Desktop services.  
Windows Virtual Desktop è un servizio completo di virtualizzazione di app e desktop in esecuzione nel cloud. È l'unica infrastruttura desktop virtuale (VDI) che offre gestione semplificata, Windows 10 multisessione, ottimizzazioni per Office 365 ProPlus e supporto per gli ambienti Servizi Desktop remoto (RDS). Distribuisci e scala i desktop e le app di Windows in Azure in pochi minuti e ottieni funzionalità integrate di sicurezza e conformità.
Ecco cosa si può fare quando si esegue Desktop virtuale Windows in Azure:
- Configurare una distribuzione di Windows 10 multisessione che offre una versione completa Windows 10 con scalabilità
- Virtualizzare Office 365 ProPlus e ottimizzarlo per l'esecuzione in scenari virtuali multiutente
- Fornire ai desktop virtuali di Windows 7 aggiornamenti della sicurezza estesi gratuiti
- Portare i desktop e le app esistenti di Servizi Desktop remoto e Windows Server in qualsiasi computer
- Virtualizzare sia i desktop che le app
- Gestire desktop e app di Windows 10, Windows Server e Windows 7 con un'esperienza di gestione unificata Per ulteriori informazioni sulle operazioni che è possibile eseguire con Windows Virtual Desktop, guardare il [video introduttivo](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Usare Windows Virtual Desktop con AzureUse Windows Virtual Desktop with Azure 
I sottoscrittori di Visual Studio ora hanno diversi modi per usare le sottoscrizioni di Azure per pagare i servizi Desktop virtuale di Windows:
- [AppMenti di Azure DevTest singoli crediti](vs-azure.md).  I sottoscrittori che ricevono singoli crediti di Azure DevTest come parte delle sottoscrizioni possono usare tali crediti per pagare i servizi Desktop virtuale di Windows.Subscribers who receive Azure DevTest individual credits as part of their subscriptions can use those credits to pay for Windows Virtual Desktop services.  L'importo del credito mensile dipende dal livello di sottoscrizione.
- Sottoscrizioni con pagamento in base al [costo di Azure DevTest.](vs-azure-payg.md)  È possibile creare sottoscrizioni di Azure e collegare uno strumento di pagamento per ottenere un modo semplice per pagare l'utilizzo di Windows Virtual Desktop.You can create Azure subscriptions and attach a payment instrument to have a seamless way to pay for your Windows Virtual Desktop usage. 
- [Offerta DevTest contratto Enterprise di Azure](azure-ea-devtest.md).  Con questa offerta, i sottoscrittori con contratti Enterprise possono pagare per Windows Virtual Desktop con Azure a prezzi scontati. 

## <a name="requirements"></a>Requisiti
Windows Virtual Desktop richiede azure Active Directory (Azure AD) a cui verranno aggiunte le macchine virtuali.  Gli utenti devono essere membri di Azure AD.  Sono disponibili due opzioni per implementare Azure AD:There are two options to implement the Azure AD:
- Servizi directory di Azure AD.  Per la maggior parte degli utenti, questa è l'opzione più semplice da implementare.
- Una macchina virtuale che esegue una promozione del controller di dominio.  Questa opzione richiede più lavoro da configurare, ma offre alla maggior parte degli utenti un costo operativo inferiore.
Per visualizzare un elenco completo dei prerequisiti per l'utilizzo di Windows Virtual Desktop, visitare la [pagina di panoramica](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)di Windows Virtual Desktop . 

## <a name="get-started"></a>Introduzione 
Quando tutti i prerequisiti sono presenti, è consigliabile completare diverse azioni per ottenere l'implementazione sul posto.  Dai un'occhiata a questi tutorial per iniziare:
- [Creare un tenant di Windows Virtual DesktopCreate a Windows Virtual Desktop tenant](https://docs.microsoft.com/azure/virtual-desktop/tenant-setup-azure-active-directory)
- [Creare un pool host](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace) usando il portale di AzureCreate a host pool using the Azure portal
- [Gestire i gruppi di app](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups) per Windows Virtual Desktop

## <a name="eligibility"></a>Idoneità
| Livello di sottoscrizione                                                 |     Canali                                            | Vantaggi                                                          | Rinnovabile?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, Retail, | Disponibile|  Sì          |
| Visual Studio Enterprise con GitHub Enterprise  | Vl | Disponibile|  Sì          |
| Visual Studio Professional (Standard) | VL, Azure, Retail                                       | Disponibile                                                             |  Sì             |
| Visual Studio Professional con GitHub Enterprise | Vl                                       | Disponibile                                        |  Sì           |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Disponibile|  Sì          |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Disponibile                                         |  Sì          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Non disponibile  | N/D |
| Visual Studio Enterprise, Visual Studio Professional (cloud mensile) | Azure | Non disponibile | N/D |

<sup>1</sup>  *Include: Not for Resale (NFR), FTE, Most Valuable Professional (MVP), Regional Director (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine*

> [!NOTE]
> Microsoft non offre più sottoscrizioni annuali di Visual Studio Professional e Visual Studio Enterprise nelle sottoscrizioni cloud. Non verrà apportata alcuna modifica all'esperienza dei clienti corrente, né alle possibilità di rinnovo, espansione, riduzione o annullamento delle sottoscrizioni esistenti. I nuovi clienti sono [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) invitati a passare a esplorare diverse opzioni per l'acquisto di Visual Studio.

Non si è certi della sottoscrizione in uso?  Connettersi [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) a per visualizzare tutte le sottoscrizioni assegnate all'indirizzo di posta elettronica. Se non sono visualizzate tutte le sottoscrizioni, è possibile che una o più sottoscrizioni siano assegnate a un indirizzo di posta elettronica diverso.  È necessario accedere con tale indirizzo di posta elettronica per visualizzare le sottoscrizioni.

## <a name="see-also"></a>Vedere anche
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione sul desktop virtuale di Windows](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Passaggi successivi
-   Se è necessario acquistare sottoscrizioni di Visual Studio, vedere:If you need to purchase Visual Studio subscriptions, check out:
     - [Prezzi per gli acquisti al dettaglio](https://visualstudio.microsoft.com/vs/pricing/) tramite Microsoft Store
     - [Programmi di contratti multilicenza](https://www.microsoft.com/licensing/default)
-   Informazioni su [Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview) 
