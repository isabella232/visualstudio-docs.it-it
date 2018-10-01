---
title: Gestione dei pacchetti VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 349dc380e23e5f76ad32631384bc4db8fceeff00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529062"
---
# <a name="managing-vspackages"></a>Gestione dei pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [gestione dei pacchetti VSPackage](https://docs.microsoft.com/visualstudio/extensibility/managing-vspackages).  
  
Nella maggior parte dei casi non è necessario preoccuparsi della gestione dei pacchetti VSPackage, poiché i modelli di progetto ed elemento registrare e caricare automaticamente il pacchetto. Tuttavia, in alcuni casi potrebbe essere necessario apprendere un po' più allo scopo di gestire il pacchetto.  
  
## <a name="using-the-experimental-instance"></a>Usare l'istanza sperimentale  
 Per altre informazioni sull'istanza sperimentale, vedere [il processo dell'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrazione e annullamento della registrazione di pacchetti VSPackage  
 Per sapere come registrare e annullare la registrazione di pacchetti VSPackage e altri tipi di estensione, vedere [la registrazione e annullamento della registrazione dei pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Il caricamento di un pacchetto VSPackage  
 Per caricare automaticamente quando un determinato che GUID CMDUICONTEXT è attivata, è possono impostare i pacchetti VSPackage. Per altre informazioni, vedere [caricamento di VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Usare AsyncPackage per caricare pacchetti VSPackage in Background  
 La classe AsyncPackage consente il caricamento in un thread in background per una migliore velocità di risposta dell'interfaccia utente in Visual Studio di pacchetto. Per altre informazioni, vedere [procedura: usare AsyncPackage per pacchetti VSPackage di caricamento in Background](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contesto dell'interfaccia utente basata su regole per le estensioni  
 Contesti dell'interfaccia utente basata su regole consente agli autori di estensioni definire le condizioni precise in cui viene attivato un contesto dell'interfaccia utente e associati i pacchetti VSPackage caricato. Per altre informazioni, vedere [procedura: basato su regole di utilizzo di contesto dell'interfaccia utente per le estensioni di Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi relativi ai pacchetti VSPackage  
 Scopri le tecniche per la risoluzione dei problemi relativi a pacchetti VSPackage che non vengono caricati o si verificano errori: [pacchetti VSPackage di risoluzione dei problemi](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)

