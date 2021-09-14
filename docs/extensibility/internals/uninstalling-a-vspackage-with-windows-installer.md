---
title: Disinstallazione di un vspackage con Windows installer | Microsoft Docs
description: Windows Il programma di installazione può disinstallare il pacchetto VSPackage invertindo l'installazione. Informazioni su come gestire le azioni personalizzate nel pacchetto Windows installer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e1c616b366e18cc6bba0bb9eb2906193022a6289
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627312"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Disinstallazione di un pacchetto VSPackage con Windows Installer
Per la maggior parte, Windows programma di installazione può disinstallare il pacchetto VSPackage semplicemente "annullando" le operazioni che ha fatto per installare il pacchetto VSPackage. Le azioni personalizzate descritte in [Comandi che devono essere eseguiti dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md) devono essere eseguite anche dopo una disinstallazione. Poiché le chiamate a devenv.exe si verificano subito prima dell'azione standard InstallFinalize sia per l'installazione che per la disinstallazione, le voci della tabella CustomAction e InstallExecuteSequence servono entrambi i casi.

> [!NOTE]
> Eseguire `devenv /setup` dopo la disinstallazione di un pacchetto MSI.

 Come regola generale, se si aggiungono azioni personalizzate a un pacchetto Windows Installer, è necessario gestire tali azioni durante la disinstallazione e il rollback. Se si aggiungono azioni personalizzate per registrare automaticamente il pacchetto VSPackage, ad esempio, è necessario aggiungere anche azioni personalizzate per annullarla.

> [!NOTE]
> Un utente può installare il pacchetto VSPackage e quindi disinstallare le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con cui è integrato. È possibile assicurarsi che la disinstallazione del pacchetto VSPackage funzioni in tale scenario eliminando le azioni personalizzate che eseguono codice con dipendenze in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestione delle condizioni di avvio in fase di disinstallazione
 L'azione standard LaunchConditions legge le righe della tabella LaunchCondition per visualizzare i messaggi di errore se le condizioni non vengono soddisfatte. Poiché le condizioni di avvio vengono in genere usate per garantire che i requisiti di sistema siano soddisfatti, è in genere possibile ignorare le condizioni di avvio durante la disinstallazione aggiungendo la condizione , alla riga `NOT Installed` LaunchConditions della tabella LaunchCondition.

 Un'alternativa consiste `OR Installed` nell'aggiungere alle condizioni di avvio che non sono importanti durante la disinstallazione. Ciò garantisce che la condizione sia sempre vera durante la disinstallazione e pertanto non verrà visualizzato il messaggio di errore della condizione di avvio.

> [!NOTE]
> `Installed`è la proprietà Windows installer impostata quando rileva che il pacchetto VSPackage è già stato installato nel sistema.

## <a name="see-also"></a>Vedi anche
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)