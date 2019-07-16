---
title: Come vengono eseguiti gli aggiornamenti dell'applicazione ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2e8a3c1054219bb7d5b0f9a9ef5e710786344e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152841"
---
# <a name="how-clickonce-performs-application-updates"></a>Come vengono eseguiti gli aggiornamenti di applicazioni con ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce Usa le informazioni sulla versione di file specificati nel manifesto di distribuzione di un'applicazione per decidere se aggiornare i file dell'applicazione. Dopo l'inizio di un aggiornamento, ClickOnce Usa una tecnica detta *patch con file* per evitare il download ridondante dei file dell'applicazione.  
  
## <a name="file-patching"></a>L'applicazione di patch di file  
 Quando si aggiorna un'applicazione, ClickOnce non scarica tutti i file per la nuova versione dell'applicazione, a meno che i file sono stati modificati. Al contrario, confronta le firme hash dei file specificati nel manifesto dell'applicazione per l'applicazione corrente rispetto alle firme contenute nel manifesto per la nuova versione. Se le firme del file sono diverse, viene scaricata la nuova versione. Se le firme corrispondono, il file non è modificato da una versione a quella successiva. In questo caso, ClickOnce consente di copiare il file esistente e lo Usa nella nuova versione dell'applicazione. Questo approccio impedisce ClickOnce di dover scaricare l'intera applicazione nuovamente, anche se solo uno o due file sono stati modificati.  
  
 Patch con file funziona anche per gli assembly che vengono scaricati su richiesta usando il <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> e <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metodi.  
  
 Se si usa Visual Studio per compilare l'applicazione, verrà generato nuove firme hash per tutti i file ogni volta che si ricompila l'intero progetto. In questo caso, verranno scaricati tutti gli assembly al client, anche se solo alcuni assembly sia stato modificato.  
  
 File dell'applicazione di patch non funziona per i file sono contrassegnati come dati e archiviati nella directory dei dati. Questi vengono sempre scaricati indipendentemente dalla firma hash del file. Per altre informazioni sulla directory dei dati, vedere [l'accesso ai dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
