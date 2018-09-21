---
title: Disinstallazione di un pacchetto VSPackage con Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c619cdeffccb6e5da37eaaf15e5542fe78c44f79
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495310"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Disinstallazione di un pacchetto VSPackage con Windows Installer
Nella maggior parte, Windows Installer possibile disinstallare il pacchetto VSPackage semplicemente di "annullamento" cosa è stato eseguito per installare il pacchetto VSPackage. Le azioni personalizzate illustrate in [comandi che devono essere eseguiti dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md) deve essere eseguito dopo una disinstallazione anche. Poiché le chiamate a devenv.exe si verificano appena prima dell'azione standard InstallFinalize mentre per l'installazione e alla disinstallazione, le voci della tabella CustomAction e InstallExecuteSequence servono entrambi i casi.  
  
> [!NOTE]
>  Eseguire `devenv /setup` dopo la disinstallazione di un pacchetto MSI.  
  
 Come regola generale, se si aggiungono le azioni personalizzate a un pacchetto Windows Installer, è necessario gestire tali azioni durante la disinstallazione e rollback. Se si aggiungono le azioni personalizzate per effettuare la registrazione automatica del pacchetto VSPackage, ad esempio, è necessario aggiungere le azioni personalizzate per annullare la registrazione, troppo.  
  
> [!NOTE]
>  È possibile che un utente di installare il pacchetto VSPackage e quindi disinstallare le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con cui è integrato. È possibile garantire che la disinstallazione di un VSPackage funziona in questo scenario, eliminando le azioni personalizzate che eseguono il codice con dipendenze su [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestione delle condizioni di avvio al momento della disinstallazione  
 L'azione standard LaunchConditions legge le righe della tabella a cui viene visualizzato errore LaunchCondition messaggi se non vengono soddisfatte le condizioni. Come condizioni di avvio in genere usate per garantire che siano soddisfatti i requisiti di sistema, è possibile ignorare le condizioni di avvio in genere durante la disinstallazione aggiungendo la condizione, `NOT Installed`, alla riga della tabella LaunchCondition LaunchConditions.  
  
 Un'alternativa consiste nell'aggiungere `OR Installed` per avviare le condizioni che non sono importanti durante la disinstallazione. Questo garantisce che la condizione sarà sempre true durante la disinstallazione e pertanto non visualizzerà il messaggio di errore di condizione di avvio.  
  
> [!NOTE]
>  `Installed` è la proprietà che Windows Installer imposta quando viene rilevato che il pacchetto VSPackage è stato installato nel sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Programma di installazione di Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)