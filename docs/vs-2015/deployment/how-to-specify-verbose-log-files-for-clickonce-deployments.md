---
title: 'Procedura: specificare i file di Log dettagliati per le distribuzioni di ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b30260267fca5b7de16316e84082fc3b464f7deb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526567"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procedura: specificare i file di log dettagliati per le distribuzioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: specificare i file di Log dettagliati per le distribuzioni ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-verbose-log-files-for-clickonce-deployments).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantiene i file di log attività per tutte le distribuzioni. Questi log documentare i dettagli relativi a installazione, l'inizializzazione, l'aggiornamento e disinstallazione di un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione. Per aumentare il livello di dettaglio che [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] operazioni di scrittura a questi file di log, usare l'Editor del Registro di sistema (**regedit.exe**) per specificare il livello di dettaglio.  
  
> [!CAUTION]
>  Se si usa in modo non corretto dell'Editor del Registro di sistema, si può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.  
  
 La procedura seguente viene descritto come specificare il livello di dettaglio per [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] file di log per l'utente corrente. Per ridurre il livello di dettaglio, rimuovere questo valore del Registro di sistema.  
  
### <a name="to-specify-verbose-log-files"></a>Per specificare file di log dettagliati  
  
1.  Aprire **Regedit.exe**.  
  
2.  Passare al nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Se necessario, creare un nuovo valore stringa denominato `LogVerbosityLevel`.  
  
4.  Impostare il `LogVerbosityLevel` valore `1`.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)



