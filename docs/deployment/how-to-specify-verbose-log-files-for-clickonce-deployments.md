---
title: Specificare i file di log dettagliati (ClickOnce distribuzione)
description: Informazioni su come specificare il livello di dettaglio per i log attività ClickOnce per l'installazione, l'inizializzazione, l'aggiornamento e la disinstallazione di una ClickOnce distribuzione.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 6b7760aa8f7916d14b7d3f5ee03978f1e2d2193a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080481"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procedura: Specificare i file di log dettagliati per le distribuzioni ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gestisce i file di log attività per tutte le distribuzioni. Questi log documentano i dettagli relativi all'installazione, all'inizializzazione, all'aggiornamento e alla disinstallazione di una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per aumentare i dettagli di scrittura in questi file di log, usare l'editor del Registro di sistema (regedit.exe) per specificare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] il livello di dettaglio.**

> [!CAUTION]
> Se si usa l'editor del Registro di sistema in modo errato, potrebbero verificarsi gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.

 Nella procedura seguente viene descritto come specificare il livello di dettaglio per i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file di log per l'utente corrente. Per ridurre il livello di dettaglio, rimuovere questo valore del Registro di sistema.

### <a name="to-specify-verbose-log-files"></a>Per specificare file di log dettagliati

1. Aprire *Regedit.exe*.

2. Passare al nodo **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.

3. Se necessario, creare un nuovo valore stringa denominato `LogVerbosityLevel` .

4. Impostare il `LogVerbosityLevel` valore su `1` .

## <a name="see-also"></a>Vedi anche
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)