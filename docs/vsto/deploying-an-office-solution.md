---
title: Distribuire una soluzione Office distribuzione
description: È possibile distribuire le soluzioni Office utilizzando ClickOnce o Windows Installer. Usando il ClickOnce, si riduce il numero di passaggi necessari per la distribuzione della soluzione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2345e66ac6d13e4110db7b660d227963bf7abae1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130676"
---
# <a name="deploy-an-office-solution"></a>Distribuire una soluzione Office distribuzione
  È possibile distribuire le soluzioni Office utilizzando ClickOnce o Windows Installer. L'utilizzo di ClickOnce consente di ridurre il numero di passaggi necessari per la distribuzione e l'aggiornamento della soluzione. Se si utilizza Windows Installer, viene mantenuto il controllo sulla modalità di installazione della soluzione e sulle pagine del programma di installazione che vengono visualizzate quando gli utenti installano la soluzione.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>Distribuire una soluzione usando ClickOnce
 Quando si effettua la distribuzione tramite ClickOnce, la soluzione viene pubblicata in una posizione centrale da cui gli utenti possono installarla ed eseguirla. È possibile aggiornare la soluzione senza dover distribuire un nuovo programma di installazione agli utenti.  Questa opzione di distribuzione è più semplice, ma non consente di visualizzare agli utenti eventuali pagine di configurazione personalizzate. Inoltre, le soluzioni devono essere installate più volte su qualsiasi computer con più di un utente. Vedere [Deploy an Office solution by using ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploy-a-solution-by-using-windows-installer"></a>Distribuire una soluzione usando il programma di Windows di installazione
 Quando una soluzione viene distribuita tramite Windows Installer, viene distribuito un programma di installazione agli utenti, il quali lo utilizzano per installare la soluzione. Con questo programma di installazione è possibile installare una soluzione per tutti gli utenti di un computer contemporaneamente, anziché solo per l'utente corrente. Questo tipo di distribuzione consente anche di avere un maggiore controllo sulle opzioni che vengono visualizzate agli utenti quando installano la soluzione. Ad esempio, è possibile mostrare un contratto di licenza oppure consentire agli utenti di installare componenti specifici di una soluzione. Tuttavia, per aggiornare la soluzione, è necessario distribuire un nuovo programma di installazione. Vedere [Deploy an Office solution by using Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="see-also"></a>Vedi anche
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Distribuire una Office di distribuzione usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Distribuire una soluzione Office usando il programma di installazione Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [Risolvere i Office distribuzione della soluzione](../vsto/troubleshooting-office-solution-deployment.md)
