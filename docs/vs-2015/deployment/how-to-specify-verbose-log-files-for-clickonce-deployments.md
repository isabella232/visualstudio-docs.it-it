---
title: 'Procedura: specificare i file di log dettagliati per le distribuzioni ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840265"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procedura: specificare i file di log dettagliati per le distribuzioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] gestisce i file di log attività per tutte le distribuzioni. Vengono registrati i dettagli del documento riguardanti l'installazione, l'inizializzazione, l'aggiornamento e la disinstallazione di una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione. Per aumentare il dettaglio che [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] scrive in questi file di log, usare l'editor del registro di sistema (**regedit.exe**) per specificare il livello di dettaglio.  
  
> [!CAUTION]
> Se si utilizza l'editor del registro di sistema in modo errato, è possibile che si verifichino gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.  
  
 Nella procedura seguente viene descritto come specificare il livello di dettaglio per i [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] file di log per l'utente corrente. Per ridurre il livello di dettaglio, rimuovere il valore del registro di sistema.  
  
### <a name="to-specify-verbose-log-files"></a>Per specificare i file di log dettagliati  
  
1. Aprire **Regedit.exe**.  
  
2. Passare al nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Se necessario, creare un nuovo valore stringa denominato `LogVerbosityLevel` .  
  
4. Impostare il `LogVerbosityLevel` valore su `1` .  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
