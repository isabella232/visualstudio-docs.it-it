---
title: 'Procedura: Specificare i file di Log dettagliati per le distribuzioni di ClickOnce | Microsoft Docs'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441612"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procedura: Specificare i file di log dettagliati per le distribuzioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantiene i file di log attività per tutte le distribuzioni. Questi log documentare i dettagli relativi a installazione, l'inizializzazione, l'aggiornamento e disinstallazione di un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione. Per aumentare il livello di dettaglio che [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] operazioni di scrittura a questi file di log, usare l'Editor del Registro di sistema (**regedit.exe**) per specificare il livello di dettaglio.  
  
> [!CAUTION]
> Se si usa in modo non corretto dell'Editor del Registro di sistema, si può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.  
  
 La procedura seguente viene descritto come specificare il livello di dettaglio per [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] file di log per l'utente corrente. Per ridurre il livello di dettaglio, rimuovere questo valore del Registro di sistema.  
  
### <a name="to-specify-verbose-log-files"></a>Per specificare file di log dettagliati  
  
1. Aprire **Regedit.exe**.  
  
2. Passare al nodo `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3. Se necessario, creare un nuovo valore stringa denominato `LogVerbosityLevel`.  
  
4. Impostare il `LogVerbosityLevel` valore `1`.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
