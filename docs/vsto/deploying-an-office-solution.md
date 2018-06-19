---
title: Distribuire una soluzione Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58e485384f80b2f0fdfc46a91caf305754a87301
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261958"
---
# <a name="deploy-an-office-solution"></a>Distribuire una soluzione Office
  È possibile distribuire le soluzioni Office utilizzando ClickOnce o Windows Installer. L'utilizzo di ClickOnce consente di ridurre il numero di passaggi necessari per la distribuzione e l'aggiornamento della soluzione. Se si utilizza Windows Installer, viene mantenuto il controllo sulla modalità di installazione della soluzione e sulle pagine del programma di installazione che vengono visualizzate quando gli utenti installano la soluzione.  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e componenti aggiuntivi VSTO ed è possibile compilarli utilizzando qualsiasi tecnologia, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="deploy-a-solution-by-using-clickonce"></a>Distribuire una soluzione tramite ClickOnce  
 Quando si effettua la distribuzione tramite ClickOnce, la soluzione viene pubblicata in una posizione centrale da cui gli utenti possono installarla ed eseguirla. È possibile aggiornare la soluzione senza dover distribuire un nuovo programma di installazione agli utenti.  Questa opzione di distribuzione è più semplice, ma non consente di visualizzare agli utenti eventuali pagine di configurazione personalizzate. Inoltre, le soluzioni devono essere installate più volte su qualsiasi computer con più di un utente. Vedere [distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="deploy-a-solution-by-using-windows-installer"></a>Distribuire una soluzione tramite Windows Installer  
 Quando una soluzione viene distribuita tramite Windows Installer, viene distribuito un programma di installazione agli utenti, il quali lo utilizzano per installare la soluzione. Con questo programma di installazione è possibile installare una soluzione per tutti gli utenti di un computer contemporaneamente, anziché solo per l'utente corrente. Questo tipo di distribuzione consente anche di avere un maggiore controllo sulle opzioni che vengono visualizzate agli utenti quando installano la soluzione. Ad esempio, è possibile mostrare un contratto di licenza oppure consentire agli utenti di installare componenti specifici di una soluzione. Tuttavia, per aggiornare la soluzione, è necessario distribuire un nuovo programma di installazione. Vedere [distribuire una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Distribuire una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Risolvere i problemi di distribuzione di soluzioni Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  