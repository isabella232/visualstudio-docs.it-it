---
title: Disinstallazione di un pacchetto VSPackage con Windows Installer Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704269"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Disinstallazione di un pacchetto VSPackage con Windows Installer
Per la maggior parte, Windows Installer può disinstallare il pacchetto VSPackage semplicemente "annullando" ciò che ha fatto per installare il pacchetto VSPackage. Le azioni personalizzate descritte in [Comandi che devono essere eseguiti dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md) devono essere eseguite anche dopo una disinstallazione. Poiché le chiamate a devenv.exe si verificano appena prima dell'azione standard InstallFinalize sia per l'installazione che per la disinstallazione, le voci della tabella CustomAction e InstallExecuteSequence servono entrambi i casi.

> [!NOTE]
> Eseguire `devenv /setup` dopo la disinstallazione di un pacchetto MSI.

 Come regola generale, se si aggiungono azioni personalizzate a un pacchetto di Windows Installer, è necessario gestire tali azioni durante la disinstallazione e il rollback. Se si aggiungono azioni personalizzate per auto-registrare il pacchetto VSPackage, ad esempio, è necessario aggiungere azioni personalizzate per annullare la registrazione, troppo.

> [!NOTE]
> È possibile per un utente installare il pacchetto VSPackage e quindi disinstallare le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con cui è integrato. È possibile garantire che la disinstallazione del pacchetto VSPackage funziona in tale scenario [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]eliminando le azioni personalizzate che eseguono codice con dipendenze su .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestione delle condizioni di avvio in fase di disinstallazioneHandling Launch Conditions at Uninstall Time
 L'azione standard LaunchConditions legge le righe della tabella LaunchCondition per visualizzare i messaggi di errore se le condizioni non vengono soddisfatte. Poiché le condizioni di avvio vengono in genere utilizzate per garantire che i `NOT Installed`requisiti di sistema siano soddisfatti, in genere è possibile ignorare le condizioni di avvio durante la disinstallazione aggiungendo la condizione , , alla riga LaunchConditions della tabella LaunchCondition.

 Un'alternativa consiste `OR Installed` nell'aggiungere alle condizioni di avvio che non sono importanti durante la disinstallazione. Ciò garantisce che la condizione sarà sempre true durante la disinstallazione e pertanto non verrà visualizzato il messaggio di errore della condizione di avvio.

> [!NOTE]
> `Installed`è la proprietà impostata da Windows Installer quando rileva che il pacchetto VSPackage è già stato installato nel sistema.

## <a name="see-also"></a>Vedere anche
- [Programma di installazione di Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)
