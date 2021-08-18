---
title: Scelta di una ClickOnce di distribuzione | Microsoft Docs
description: Informazioni sulle strategie per la distribuzione di un'ClickOnce e su come scegliere una strategia a seconda del tipo di applicazione che si sta distribuendo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e3b518218204aa6eaeb06bae1cb519f8b4270dc1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073916"
---
# <a name="choose-a-clickonce-deployment-strategy"></a>Scegliere una strategia di distribuzione ClickOnce
Per la distribuzione di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono disponibili tre diverse strategie. La scelta dipende principalmente dal tipo di applicazione che si desidera distribuire. Le tre strategie di distribuzione sono elencate di seguito:

- Installazione dal Web o da una condivisione di rete

- Installazione da un CD

- Avvio dell'applicazione dal Web o da una condivisione di rete

    > [!NOTE]
    > Oltre alla scelta di una strategia di distribuzione, sarà anche possibile scegliere una strategia per gli aggiornamenti dell'applicazione. Per altre informazioni, vedere [Scegliere una strategia di ClickOnce di aggiornamento.](../deployment/choosing-a-clickonce-update-strategy.md)

## <a name="install-from-the-web-or-a-network-share"></a>Installazione dal Web o da una condivisione di rete
 Se si utilizza questa strategia, l'applicazione verrà distribuita in un server Web o in una condivisione file di rete. Quando un utente finale desidera installare l'applicazione, fa clic su un'icona su una pagina Web oppure fa doppio clic su un'icona nella condivisione di rete. L'applicazione viene quindi scaricata, installata e avviata sul computer. Gli elementi vengono aggiunti al **menu Start** e al gruppo **Installazione applicazioni** nel **Pannello di controllo**.

 Poiché dipende dalla connettività di rete, questa strategia è particolarmente consigliata per le applicazioni che devono essere distribuite a utenti che hanno accesso a una rete LAN o a una connessione Internet ad alta velocità.

 Se si distribuisce l'applicazione dal Web, è possibile passare argomenti all'applicazione qualora venga attivata utilizzando un URL. Per altre informazioni, vedere [Procedura: Recuperare informazioni sulla stringa di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Non è possibile passare argomenti a un'applicazione attivata utilizzando gli altri metodi descritti in questo documento.

 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], fare clic su **Dal Web** oppure su **Da un percorso UNC o condivisione file** nella pagina **Specificare come verrà installata l'applicazione dagli utenti** della Pubblicazione guidata.

 Questa è la strategia di distribuzione predefinita.

## <a name="start-the-application-from-the-web-or-a-network-share"></a>Avvio dell'applicazione dal Web o da una condivisione di rete
 Questa strategia è simile alla prima, tranne per il fatto che in questo caso l'applicazione si comporta come un'applicazione Web. Quando l'utente fa clic su collegamento in una pagina Web, oppure fa doppio clic su un'icona della condivisione file, l'applicazione viene avviata. Quando viene chiusa dall'utente, l'applicazione non è più disponibile nel computer locale. Nessun elemento viene aggiunto al **menu Start** o al gruppo **Installazione applicazioni** del **Pannello di controllo**.

> [!NOTE]
> Tecnicamente, l'applicazione viene scaricata e installata in una cache dell'applicazione sul computer locale, analogamente a un'applicazione Web scaricata nella cache Web. Come per la cache Web, alla fine viene eseguito lo scavenging dei file dalla cache dell'applicazione. La percezione dell'utente, tuttavia, è che l'applicazione venga eseguita dal Web o dalla condivisione file.

 Questa strategia è particolarmente consigliata per le applicazioni che vengono utilizzate poco di frequente, ad esempio uno strumento per i benefit dei dipendenti che viene eseguito solo una volta all'anno.

 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], fare clic su **Non installare l'applicazione** nella pagina **Installa o esegui dal Web** della Pubblicazione guidata.

 Per attivare manualmente questa strategia di distribuzione, modificare il tag **install** nel manifesto di distribuzione. Il valore può essere **true** o **false**. In *Mage.exe* utilizzare l'opzione **Solo online** dell'elenco a discesa **Tipo di applicazione**.

## <a name="install-from-a-cd"></a>Installazione da un CD
 Se si utilizza questa strategia l'applicazione viene distribuita su un supporto rimovibile quale CD-ROM o DVD. Come per l'opzione precedente, quando l'utente sceglie di installare l'applicazione, questa viene installata e avviata e gli elementi vengono aggiunti al **menu Start** e al gruppo **Installazione applicazioni** del **Pannello di controllo**.

 Questa strategia è particolarmente consigliata per le applicazioni che verranno distribuite a utenti che non dispongono di una connettività di rete permanente o con connessioni a larghezza di banda limitata. Dal momento che l'applicazione viene installata da un supporto rimovibile, per l'installazione non è necessaria alcuna connessione di rete, che è comunque necessaria per gli aggiornamenti dell'applicazione.

 Per attivare questa strategia di distribuzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], fare clic su **Da CD-ROM o DVD-ROM** nella pagina **Specificare come verrà installata l'applicazione dagli utenti** della Pubblicazione guidata.

 Per attivare manualmente questa strategia di distribuzione, modificare il tag **deploymentProvider** nel manifesto di distribuzione. In Visual Studio questa proprietà è esposta come **URL installazione** nella pagina **Pubblica** di Progettazione progetti. In *Mage.exe* corrisponde invece all'opzione **Start Location**.

## <a name="web-browser-support"></a>Supporto Web browser
 Le applicazioni destinate a .NET Framework 3.5 possono essere installate utilizzando qualsiasi browser.

 Le applicazioni destinate a .NET Framework 2.0 richiedono Internet Explorer.

## <a name="see-also"></a>Vedi anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Procedura: Pubblicare un'ClickOnce con la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Protezione di ClickOnce applicazioni](../deployment/securing-clickonce-applications.md)