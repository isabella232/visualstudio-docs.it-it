---
title: Gestione dei pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c44b31eb8f160695589dda79f19e10389490c38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944020"
---
# <a name="manage-vspackages"></a>Gestire i pacchetti VSPackage
Nella maggior parte dei casi non è necessario preoccuparsi della gestione dei pacchetti VSPackage, poiché i modelli di progetto ed elemento registrare e caricare automaticamente il pacchetto. Tuttavia, in alcuni casi potrebbe essere necessario apprendere un po' più allo scopo di gestire il pacchetto.  
  
## <a name="use-the-experimental-instance"></a>Usare l'istanza sperimentale  
 Per altre informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="register-and-unregister-vspackages"></a>Registrare e annullare la registrazione di pacchetti VSPackage  
 Per sapere come registrare e annullare la registrazione di pacchetti VSPackage e altri tipi di estensione, vedere [registrare e annullare la registrazione di pacchetti VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="load-a-vspackage"></a>Caricare un pacchetto VSPackage  
 Per caricare automaticamente quando un determinato che GUID CMDUICONTEXT è attivata, è possono impostare i pacchetti VSPackage. Per altre informazioni, vedere [VSPackage carico](../extensibility/loading-vspackages.md).  
  
## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Usare AsyncPackage per caricare pacchetti VSPackage in background  
 Il `AsyncPackage` classe consente il caricamento del pacchetto in un thread in background per una migliore velocità di risposta dell'interfaccia utente in Visual Studio. Per altre informazioni, vedere [Procedura: Usare AsyncPackage per caricare pacchetti VSPackage in background](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Regola in base al contesto dell'interfaccia utente per le estensioni  
 Contesti dell'interfaccia utente basata su regole consente agli autori di estensioni definire le condizioni precise in cui viene attivato un contesto dell'interfaccia utente e associati i pacchetti VSPackage caricato. Per altre informazioni, vedere [Procedura: Usare regole in base al contesto dell'interfaccia utente per le estensioni di Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnose-extension-performance"></a>Diagnosticare le prestazioni delle estensioni  
Le estensioni possono influire sulle prestazioni di caricamento di avvio e di soluzione. Informazioni su come viene calcolato impatto di estensione di Visual Studio e come possono essere analizzati in locale per verificare se un'estensione può essere visualizzata come alcun impatto sull'estensione delle prestazioni. Per altre informazioni, vedere [Procedura: Diagnosticare le prestazioni delle estensioni](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshoot-vspackages"></a>Risolvere i problemi di pacchetti VSPackage  
 Scopri le tecniche per la risoluzione dei problemi relativi a pacchetti VSPackage che non vengono caricati o si verificano errori: [Risolvere i problemi di pacchetti VSPackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)