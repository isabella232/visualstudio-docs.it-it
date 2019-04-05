---
title: Scelta di una strategia di distribuzione ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 619d70b79d75cc45add0d541cd081d9ac0f258d5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966072"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Scelta di una strategia di distribuzione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la distribuzione di un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sono disponibili tre diverse strategie. La scelta dipende principalmente dal tipo di applicazione che si desidera distribuire. Le tre strategie di distribuzione sono elencate di seguito:  
  
-   Installazione dal Web o da una condivisione di rete  
  
-   Installazione da un CD  
  
-   Avvio dell'applicazione dal Web o da una condivisione di rete  
  
    > [!NOTE]
    >  Oltre alla scelta di una strategia di distribuzione, sarà anche possibile scegliere una strategia per gli aggiornamenti dell'applicazione. Per altre informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Installazione dal Web o da una condivisione di rete  
 Se si utilizza questa strategia, l'applicazione verrà distribuita in un server Web o in una condivisione file di rete. Quando un utente finale desidera installare l'applicazione, fa clic su un'icona su una pagina Web oppure fa doppio clic su un'icona nella condivisione di rete. L'applicazione viene quindi scaricata, installata e avviata sul computer. Gli elementi vengono aggiunti al **menu Start** e al gruppo **Installazione applicazioni** nel **Pannello di controllo**.  
  
 Poiché dipende dalla connettività di rete, questa strategia è particolarmente consigliata per le applicazioni che devono essere distribuite a utenti che hanno accesso a una rete LAN o a una connessione Internet ad alta velocità.  
  
 Se si distribuisce l'applicazione dal Web, è possibile passare argomenti all'applicazione qualora venga attivata utilizzando un URL. Per altre informazioni, vedere [Procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Non è possibile passare argomenti a un'applicazione attivata utilizzando gli altri metodi descritti in questo documento.  
  
 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], fare clic su **Dal Web** oppure su **Da un percorso UNC o condivisione file** nella pagina **Specificare come verrà installata l'applicazione dagli utenti** della Pubblicazione guidata.  
  
 Questa è la strategia di distribuzione predefinita.  
  
## <a name="install-from-a-cd"></a>Installazione da un CD  
 Se si utilizza questa strategia l'applicazione viene distribuita su un supporto rimovibile quale CD-ROM o DVD. Come per l'opzione precedente, quando l'utente sceglie di installare l'applicazione, questa viene installata e avviata e gli elementi vengono aggiunti al **menu Start** e al gruppo **Installazione applicazioni** del **Pannello di controllo**.  
  
 Questa strategia è particolarmente consigliata per le applicazioni che verranno distribuite a utenti che non dispongono di una connettività di rete permanente o con connessioni a larghezza di banda limitata. Dal momento che l'applicazione viene installata da un supporto rimovibile, per l'installazione non è necessaria alcuna connessione di rete, che è comunque necessaria per gli aggiornamenti dell'applicazione.  
  
 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], fare clic su **Da CD-ROM o DVD-ROM** nella pagina **Specificare come verrà installata l'applicazione dagli utenti** della Pubblicazione guidata.  
  
 Per attivare manualmente questa strategia di distribuzione, modificare il tag **deploymentProvider** nel manifesto di distribuzione. In Visual Studio questa proprietà è esposta come **URL installazione** nella pagina **Pubblica** di Progettazione progetti. È in Mage.exe **percorso iniziale**.)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Avvio dell'applicazione dal Web o da una condivisione di rete  
 Questa strategia è simile alla prima, tranne per il fatto che in questo caso l'applicazione si comporta come un'applicazione Web. Quando l'utente fa clic su collegamento in una pagina Web, oppure fa doppio clic su un'icona della condivisione file, l'applicazione viene avviata. Quando viene chiusa dall'utente, l'applicazione non è più disponibile nel computer locale. Nessun elemento viene aggiunto al **menu Start** o al gruppo **Installazione applicazioni** del **Pannello di controllo**.  
  
> [!NOTE]
>  Tecnicamente, l'applicazione viene scaricata e installata in una cache dell'applicazione sul computer locale, analogamente a un'applicazione Web scaricata nella cache Web. Come per la cache Web, alla fine viene eseguito lo scavenging dei file dalla cache dell'applicazione. La percezione dell'utente, tuttavia, è che l'applicazione venga eseguita dal Web o dalla condivisione file.  
  
 Questa strategia è particolarmente consigliata per le applicazioni che vengono utilizzate poco di frequente, ad esempio uno strumento per i benefit dei dipendenti che viene eseguito solo una volta all'anno.  
  
 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], fare clic su **Non installare l'applicazione** nella pagina **Installa o esegui dal Web** della Pubblicazione guidata.  
  
 Per attivare manualmente questa strategia di distribuzione, modificare il tag **install** nel manifesto di distribuzione. Il valore può essere **true** o **false**. In Mage.exe, usare il **solo in linea** opzione il **tipo di applicazione** elenco.)  
  
## <a name="web-browser-support"></a>Supporto Web browser  
 Le applicazioni destinate a .NET Framework 3.5 possono essere installate utilizzando qualsiasi browser.  
  
 Le applicazioni destinate a .NET Framework 2.0 richiedono Internet Explorer.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Sicurezza di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
