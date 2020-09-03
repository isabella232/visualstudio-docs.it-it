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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185275"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opzioni della riga di comando devenv per lo sviluppo di pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente agli sviluppatori di automatizzare le attività dalla riga di comando durante l'esecuzione di devenv.exe, il file che avvia Visual Studio Integrated Development Environment (IDE).  
  
 Le attività includono:  
  
- Distribuzione di applicazioni in configurazioni predefinite dall'esterno dell'IDE.  
  
- Creazione automatica di progetti mediante impostazioni di compilazione predefinite o configurazioni di debug.  
  
- Caricamento dell'IDE in configurazioni specifiche, tutto dall'esterno dell'IDE. Inoltre, è possibile personalizzare l'IDE al momento dell'avvio.  
  
## <a name="guidelines-for-switches"></a>Linee guida per le opzioni  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la documentazione descrive le opzioni della riga di comando devenv a livello di utente. Per ulteriori informazioni, vedere [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md). Devenv supporta inoltre opzioni aggiuntive della riga di comando utili per lo sviluppo, la distribuzione e il debug di VSPackage.  
  
|Opzione della riga di comando|Descrizione|  
|--------------------------|-----------------|  
|/safemode|Viene avviato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità provvisoria, caricando solo l'IDE e i servizi predefiniti. L'opzione/safemode impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] avvio, garantendo in tal modo l'esecuzione stabile.<br /><br /> Questa opzione non accetta argomenti.|  
|/resetskippkgs|Cancella tutte le opzioni di caricamento ignorate che sono state aggiunte dagli utenti che desiderano evitare il caricamento di pacchetti VSPackage problematici, quindi avvia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . La presenza di un tag SkipLoading disabilita il caricamento di un pacchetto VSPackage. La cancellazione del tag consente di riabilitare il caricamento del pacchetto VSPackage.<br /><br /> Questa opzione non accetta argomenti.|  
|/rootsuffix|Inizia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando un percorso alternativo. Il comando seguente viene eseguito dal collegamento creato dal programma di [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] installazione:<br /><br /> devenv/RootSuffix Exp<br /><br /> In questo caso, exp identifica una posizione con un determinato suffisso, ad esempio 10.0 Exp anziché 10,0. L'istanza sperimentale consente di eseguire il debug di un pacchetto VSPackage separatamente dall'istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utilizzata per scrivere il codice.<br /><br /> Questa opzione può assumere qualsiasi stringa che identifichi un percorso creato con VSRegEx.exe. Per ulteriori informazioni, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).|  
|/splash|Mostra la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schermata iniziale come di consueto e quindi Visualizza una finestra di messaggio prima di visualizzare l'IDE principale. La finestra di messaggio consente di esaminare la schermata iniziale per verificare la presenza di un'icona di prodotto VSPackage, ad esempio.<br /><br /> Questa opzione non accetta argomenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di opzioni della riga di comando](../extensibility/adding-command-line-switches.md)   
 [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
