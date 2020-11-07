---
title: Specificare i file di log dettagliati (distribuzioni ClickOnce)
description: Informazioni su come specificare il livello di dettaglio per i log attività gestiti da ClickOnce per l'installazione, l'inizializzazione, l'aggiornamento e la disinstallazione di una distribuzione ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0da285cfef49bd495fbecf39131e49cacd0476a5
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350920"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procedura: Specificare i file di log dettagliati per le distribuzioni ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gestisce i file di log attività per tutte le distribuzioni. Vengono registrati i dettagli del documento riguardanti l'installazione, l'inizializzazione, l'aggiornamento e la disinstallazione di una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per aumentare il dettaglio che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scrive in questi file di log, usare l'editor del registro di sistema ( *regedit.exe* ) per specificare il livello di dettaglio.

> [!CAUTION]
> Se si utilizza l'editor del registro di sistema in modo errato, è possibile che si verifichino gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.

 Nella procedura seguente viene descritto come specificare il livello di dettaglio per i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file di log per l'utente corrente. Per ridurre il livello di dettaglio, rimuovere il valore del registro di sistema.

### <a name="to-specify-verbose-log-files"></a>Per specificare i file di log dettagliati

1. Aprire *Regedit.exe*.

2. Passare al nodo **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.

3. Se necessario, creare un nuovo valore stringa denominato `LogVerbosityLevel` .

4. Impostare il `LogVerbosityLevel` valore su `1` .

## <a name="see-also"></a>Vedere anche
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)