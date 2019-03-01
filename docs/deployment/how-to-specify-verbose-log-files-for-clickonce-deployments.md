---
title: 'Procedura: specificare i file di Log dettagliati per le distribuzioni di ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ffc7fbdace660a894352623a3ff8765a165b5556
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619498"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Procedura: Specificare i file di log dettagliati per le distribuzioni ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene i file di log attività per tutte le distribuzioni. Questi log documentare i dettagli relativi a installazione, l'inizializzazione, l'aggiornamento e disinstallazione di un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per aumentare il livello di dettaglio che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] operazioni di scrittura a questi file di log, usare l'Editor del Registro di sistema (*regedit.exe*) per specificare il livello di dettaglio.

> [!CAUTION]
>  Se si usa in modo non corretto dell'Editor del Registro di sistema, si può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.

 La procedura seguente viene descritto come specificare il livello di dettaglio per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file di log per l'utente corrente. Per ridurre il livello di dettaglio, rimuovere questo valore del Registro di sistema.

### <a name="to-specify-verbose-log-files"></a>Per specificare file di log dettagliati

1.  Aprire *Regedit.exe*.

2.  Passare al nodo **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.

3.  Se necessario, creare un nuovo valore stringa denominato `LogVerbosityLevel`.

4.  Impostare il `LogVerbosityLevel` valore `1`.

## <a name="see-also"></a>Vedere anche
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)