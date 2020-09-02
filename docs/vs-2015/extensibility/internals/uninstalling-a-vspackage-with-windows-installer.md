---
title: Disinstallazione di un pacchetto VSPackage con Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a309779850dd33b77b426beb5627f61c40c2c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675235"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Disinstallazione di un pacchetto VSPackage con Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nella maggior parte dei casi, Windows Installer possibile disinstallare il pacchetto VSPackage semplicemente eseguendo l'operazione di installazione del pacchetto VSPackage. Le azioni personalizzate illustrate in [comandi che devono essere eseguite dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md) devono essere eseguite anche dopo una disinstallazione. Poiché le chiamate a devenv.exe si verificano subito prima dell'azione standard InstallFinalize per l'installazione e la disinstallazione, le voci della tabella CustomAction e InstallExecuteSequence servono entrambi i casi.  
  
> [!NOTE]
> Eseguire `devenv /setup` dopo la disinstallazione di un pacchetto MSI.  
  
 Come regola generale, se si aggiungono azioni personalizzate a un pacchetto di Windows Installer, è necessario gestire tali azioni durante la disinstallazione e il rollback. Se si aggiungono azioni personalizzate per registrare autonomamente il pacchetto VSPackage, ad esempio, è necessario aggiungere anche azioni personalizzate per annullare la registrazione.  
  
> [!NOTE]
> È possibile che un utente possa installare il pacchetto VSPackage e quindi disinstallare le versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con cui è integrato. È possibile garantire che la disinstallazione del pacchetto VSPackage funzioni in tale scenario eliminando azioni personalizzate che eseguono codice con dipendenze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestione delle condizioni di avvio in fase di disinstallazione  
 L'azione LaunchConditions standard legge le righe della tabella LaunchCondition per visualizzare i messaggi di errore se le condizioni non vengono soddisfatte. Poiché le condizioni di avvio vengono in genere utilizzate per garantire che siano soddisfatti i requisiti di sistema, in genere è possibile ignorare le condizioni di avvio durante la disinstallazione aggiungendo la condizione, `NOT Installed` , alla riga LaunchConditions della tabella LaunchCondition.  
  
 Un'alternativa consiste nell'aggiungere `OR Installed` alle condizioni di avvio che non sono importanti durante la disinstallazione. In questo modo si garantisce che la condizione sia sempre true durante la disinstallazione e pertanto non visualizzerà il messaggio di errore relativo alla condizione di avvio.  
  
> [!NOTE]
> `Installed` Proprietà Windows Installer imposta quando rileva che il pacchetto VSPackage è già stato installato nel sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](https://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)
