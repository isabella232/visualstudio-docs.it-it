---
title: Distribuire una soluzione OfficeDeploy an Office solution
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24ec10c42935ac961218f910fbef98d51f5f5569
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416510"
---
# <a name="deploy-an-office-solution"></a>Distribuire una soluzione OfficeDeploy an Office solution
  È possibile distribuire le soluzioni Office utilizzando ClickOnce o Windows Installer. L'utilizzo di ClickOnce consente di ridurre il numero di passaggi necessari per la distribuzione e l'aggiornamento della soluzione. Se si utilizza Windows Installer, viene mantenuto il controllo sulla modalità di installazione della soluzione e sulle pagine del programma di installazione che vengono visualizzate quando gli utenti installano la soluzione.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>Distribuire una soluzione tramite ClickOnceDeploy a solution by using ClickOnce
 Quando si effettua la distribuzione tramite ClickOnce, la soluzione viene pubblicata in una posizione centrale da cui gli utenti possono installarla ed eseguirla. È possibile aggiornare la soluzione senza dover distribuire un nuovo programma di installazione agli utenti.  Questa opzione di distribuzione è più semplice, ma non consente di visualizzare agli utenti eventuali pagine di configurazione personalizzate. Inoltre, le soluzioni devono essere installate più volte su qualsiasi computer con più di un utente. Vedere [Distribuire una soluzione Office utilizzando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploy-a-solution-by-using-windows-installer"></a>Distribuire una soluzione tramite Windows InstallerDeploy a solution by using Windows Installer
 Quando una soluzione viene distribuita tramite Windows Installer, viene distribuito un programma di installazione agli utenti, il quali lo utilizzano per installare la soluzione. Con questo programma di installazione è possibile installare una soluzione per tutti gli utenti di un computer contemporaneamente, anziché solo per l'utente corrente. Questo tipo di distribuzione consente anche di avere un maggiore controllo sulle opzioni che vengono visualizzate agli utenti quando installano la soluzione. Ad esempio, è possibile mostrare un contratto di licenza oppure consentire agli utenti di installare componenti specifici di una soluzione. Tuttavia, per aggiornare la soluzione, è necessario distribuire un nuovo programma di installazione. Vedere [Distribuire una soluzione Office utilizzando Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="see-also"></a>Vedere anche
- [Proteggere le soluzioni OfficeSecure Office solutions](../vsto/securing-office-solutions.md)
- [Distribuire una soluzione Office tramite ClickOnceDeploy an Office solution by using ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Distribuire una soluzione Office tramite Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [Risolvere i problemi relativi alla distribuzione di soluzioni OfficeTroubleshoot Office solution deployment](../vsto/troubleshooting-office-solution-deployment.md)
