---
title: Disinstallazione di un pacchetto VSPackage con Windows Installer | Microsoft Docs
description: Windows Installer possibile disinstallare il pacchetto VSPackage invertendo l'installazione. Informazioni su come gestire azioni personalizzate nel pacchetto di Windows Installer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89a3ed681f51b392e076cff0fcb06b2f868c0aa5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888992"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Disinstallazione di un pacchetto VSPackage con Windows Installer
Nella maggior parte dei casi, Windows Installer possibile disinstallare il pacchetto VSPackage semplicemente eseguendo l'operazione di installazione del pacchetto VSPackage. Le azioni personalizzate illustrate in [comandi che devono essere eseguite dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md) devono essere eseguite anche dopo una disinstallazione. Poiché le chiamate a devenv.exe si verificano subito prima dell'azione standard InstallFinalize per l'installazione e la disinstallazione, le voci della tabella CustomAction e InstallExecuteSequence servono entrambi i casi.

> [!NOTE]
> Eseguire `devenv /setup` dopo la disinstallazione di un pacchetto MSI.

 Come regola generale, se si aggiungono azioni personalizzate a un pacchetto di Windows Installer, è necessario gestire tali azioni durante la disinstallazione e il rollback. Se si aggiungono azioni personalizzate per registrare autonomamente il pacchetto VSPackage, ad esempio, è necessario aggiungere anche azioni personalizzate per annullare la registrazione.

> [!NOTE]
> È possibile che un utente possa installare il pacchetto VSPackage e quindi disinstallare le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con cui è integrato. È possibile garantire che la disinstallazione del pacchetto VSPackage funzioni in tale scenario eliminando azioni personalizzate che eseguono codice con dipendenze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestione delle condizioni di avvio in fase di disinstallazione
 L'azione LaunchConditions standard legge le righe della tabella LaunchCondition per visualizzare i messaggi di errore se le condizioni non vengono soddisfatte. Poiché le condizioni di avvio vengono in genere utilizzate per garantire che siano soddisfatti i requisiti di sistema, in genere è possibile ignorare le condizioni di avvio durante la disinstallazione aggiungendo la condizione, `NOT Installed` , alla riga LaunchConditions della tabella LaunchCondition.

 Un'alternativa consiste nell'aggiungere `OR Installed` alle condizioni di avvio che non sono importanti durante la disinstallazione. In questo modo si garantisce che la condizione sia sempre true durante la disinstallazione e pertanto non visualizzerà il messaggio di errore relativo alla condizione di avvio.

> [!NOTE]
> `Installed` Proprietà Windows Installer imposta quando rileva che il pacchetto VSPackage è già stato installato nel sistema.

## <a name="see-also"></a>Vedi anche
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)