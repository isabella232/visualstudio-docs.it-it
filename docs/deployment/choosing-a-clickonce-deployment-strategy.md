---
title: Scelta di una strategia di distribuzione ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c70490420855bdd160384b75d08cc27fd73e966a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079574"
---
# <a name="choose-a-clickonce-deployment-strategy"></a>Scegliere una strategia di distribuzione ClickOnce
Per la distribuzione di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono disponibili tre diverse strategie. La scelta dipende principalmente dal tipo di applicazione che si desidera distribuire. Le tre strategie di distribuzione sono elencate di seguito:  
  
-   Installazione dal Web o da una condivisione di rete  
  
-   Installazione da un CD  
  
-   Avvio dell'applicazione dal Web o da una condivisione di rete  
  
    > [!NOTE]
    >  Oltre alla scelta di una strategia di distribuzione, sarà anche possibile scegliere una strategia per gli aggiornamenti dell'applicazione. Per altre informazioni, vedere [sceglie una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Installazione dal Web o da una condivisione di rete  
 Se si utilizza questa strategia, l'applicazione verrà distribuita in un server Web o in una condivisione file di rete. Quando un utente finale desidera installare l'applicazione, fa clic su un'icona su una pagina Web oppure fa doppio clic su un'icona nella condivisione di rete. L'applicazione viene quindi scaricata, installata e avviata sul computer. Gli elementi vengono aggiunti per il **avviare** menu e **Aggiungi / Rimuovi programmi** in **Pannello di controllo**.  
  
 Poiché dipende dalla connettività di rete, questa strategia è particolarmente consigliata per le applicazioni che devono essere distribuite a utenti che hanno accesso a una rete LAN o a una connessione Internet ad alta velocità.  
  
 Se si distribuisce l'applicazione dal Web, è possibile passare argomenti all'applicazione qualora venga attivata utilizzando un URL. Per altre informazioni, vedere [procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Non è possibile passare argomenti a un'applicazione attivata utilizzando gli altri metodi descritti in questo documento.  
  
 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], fare clic su **dal Web** o **condivisione file o percorso UNC da un** sulla **modalità di installazione** pagina della procedura guidata di pubblicazione.  
  
 Questa è la strategia di distribuzione predefinita.  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Avviare l'applicazione dal Web o da una condivisione di rete  
 Questa strategia è simile alla prima, tranne per il fatto che in questo caso l'applicazione si comporta come un'applicazione Web. Quando l'utente fa clic su collegamento in una pagina Web, oppure fa doppio clic su un'icona della condivisione file, l'applicazione viene avviata. Quando viene chiusa l'applicazione, non è più disponibile nel computer locale. viene aggiunto nulla al **avviare** dal menu o **Aggiungi / Rimuovi programmi** nel **Pannello di controllo**.  
  
> [!NOTE]
>  Tecnicamente, l'applicazione viene scaricata e installata in una cache dell'applicazione sul computer locale, analogamente a un'applicazione Web scaricata nella cache Web. Come per la cache Web, alla fine viene eseguito lo scavenging dei file dalla cache dell'applicazione. La percezione dell'utente, tuttavia, è che l'applicazione venga eseguita dal Web o dalla condivisione file.  
  
 Questa strategia è particolarmente consigliata per le applicazioni che vengono utilizzate poco di frequente, ad esempio uno strumento per i benefit dei dipendenti che viene eseguito solo una volta all'anno.  
  
 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], fare clic su **non si installa l'applicazione** sul **installa o Esegui dal Web** pagina della procedura guidata di pubblicazione.  
  
 Per attivare manualmente questa strategia di distribuzione, modificare il **installare** tag nel manifesto di distribuzione. (Il valore può essere **true** oppure **false**. In *Mage.exe*, utilizzare il **solo in linea** opzione il **tipo di applicazione** elenco.)  

## <a name="install-from-a-cd"></a>Installazione da un CD  
 Se si utilizza questa strategia l'applicazione viene distribuita su un supporto rimovibile quale CD-ROM o DVD. Come con l'opzione precedente, quando l'utente sceglie di installare l'applicazione, viene installato e avviato e gli elementi vengono aggiunti per il **avviare** menu e **Aggiungi / Rimuovi programmi** in **controllo Pannello**.  
  
 Questa strategia è particolarmente consigliata per le applicazioni che verranno distribuite a utenti che non dispongono di una connettività di rete permanente o con connessioni a larghezza di banda limitata. Dal momento che l'applicazione viene installata da un supporto rimovibile, per l'installazione non è necessaria alcuna connessione di rete, che è comunque necessaria per gli aggiornamenti dell'applicazione.  
  
 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], fare clic su **da CD-ROM o DVD-ROM** sul **modalità di installazione** pagina della procedura guidata di pubblicazione.  
  
 Per attivare manualmente questa strategia di distribuzione, modificare il **deploymentProvider** tag nel manifesto di distribuzione. (In Visual Studio, questa proprietà viene esposta come **URL di installazione** nel **Publish** pagina della finestra di Progettazione progetti. In *Mage.exe* risulta **percorso iniziale**.)  
  
## <a name="web-browser-support"></a>Supporto del browser Web  
 Le applicazioni destinate a .NET Framework 3.5 possono essere installate utilizzando qualsiasi browser.  
  
 Le applicazioni destinate a .NET Framework 2.0 richiedono Internet Explorer.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione e protezione ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Procedura: pubblicare un'applicazione ClickOnce con la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)