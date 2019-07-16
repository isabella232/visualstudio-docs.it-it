---
title: Opzioni della riga di comando devenv per lo sviluppo di VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185275"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opzioni della riga di comando devenv per lo sviluppo di pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente agli sviluppatori di automatizzare le attività dalla riga di comando durante l'esecuzione devenv.exe, il file che inizia l'ambiente di sviluppo integrato (IDE) di Visual Studio.  
  
 Le attività includono:  
  
- Distribuzione di applicazioni in configurazioni predefinite all'esterno dell'IDE.  
  
- Compilazione di progetti usando set di impostazioni automaticamente le impostazioni di compilazione o le configurazioni di debug.  
  
- Caricamento l'IDE in configurazioni specifiche, tutto all'esterno dell'IDE. Inoltre, è possibile personalizzare l'IDE all'avvio.  
  
## <a name="guidelines-for-switches"></a>Linee guida per le opzioni  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la documentazione descrive le opzioni della riga di comando devenv a livello di utente. Per altre informazioni, vedere [opzioni della riga di comando Devenv](../ide/reference/devenv-command-line-switches.md). Devenv supporta anche altre opzioni della riga di comando che sono utili con VSPackage lo sviluppo, distribuzione e debug.  
  
|Opzione della riga di comando|DESCRIZIONE|  
|--------------------------|-----------------|  
|/safemode|Avvia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità provvisoria, caricando solo l'IDE predefinito e i servizi. Il commutatore /safemode impedisce a tutti i pacchetti VSPackage di terze parti di caricamento quando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene avviato, garantendo un'esecuzione stabile.<br /><br /> Questa opzione non accetta argomenti.|  
|/resetskippkgs|Cancella tutto ignorare le opzioni di caricamento che sono stati aggiunti dagli utenti che vogliono evitare il caricamento di VSPackage problematici, quindi avvia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. La presenza di un tag SkipLoading disabilita il caricamento di un pacchetto VSPackage. La cancellazione del tag riabilita il caricamento del pacchetto VSPackage.<br /><br /> Questa opzione non accetta argomenti.|  
|/rootsuffix|Avvia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando un percorso alternativo. Il seguente comando viene eseguito mediante il collegamento creato dal [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] programma di installazione:<br /><br /> devenv /RootSuffix exp<br /><br /> In questo caso, exp identifica una posizione con un suffisso specifico, ad esempio 10.0Exp anziché a 10.0. L'istanza sperimentale che consente di eseguire il debug di un pacchetto VSPackage separatamente dall'istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che usa per scrivere codice.<br /><br /> Questa opzione può accettare qualsiasi stringa che identifica un percorso che è stato creato con VSRegEx.exe. Per altre informazioni, vedere [il processo dell'istanza sperimentale](../extensibility/the-experimental-instance.md).|  
|/Splash|Viene illustrato il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schermata iniziale come di consueto e quindi visualizza una finestra di messaggio prima di visualizzare l'IDE principale. La finestra di messaggio consente di esaminare la schermata iniziale, per cercare un'icona di prodotto di VSPackage, ad esempio.<br /><br /> Questa opzione non accetta argomenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta della riga di comando](../extensibility/adding-command-line-switches.md)   
 [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
