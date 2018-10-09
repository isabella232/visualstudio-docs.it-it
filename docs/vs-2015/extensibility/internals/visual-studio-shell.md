---
title: Shell di Visual Studio | Microsoft Docs
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
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d96d4204e105324a9c209f74f9aee160c3eddde
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519680"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Visual Studio Shell](https://docs.microsoft.com/visualstudio/extensibility/internals/visual-studio-shell).  
  
Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell è l'agente primario di integrazione in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. La shell fornisce la funzionalità necessaria per abilitare i pacchetti VSPackage condividere i servizi comuni. Poiché l'obiettivo dell'architettura di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] consiste nel vest funzionalità principale in VSPackage, la shell è un framework per offrire funzionalità di base e supportare comunicazione incrociata tra pacchetti VSPackage relativo componente.  
  
## <a name="shell-responsibilities"></a>Responsabilità della shell  
 La shell ha la responsabilità principali seguenti:  
  
-   Supporto (tramite le interfacce COM) elementi di base dell'interfaccia utente (UI). Questi includono predefinito menu e barre degli strumenti, le cornici della finestra di documento o finestre figlio di interfaccia a documenti multipli (MDI) e le cornici della finestra degli strumenti e supporto per l'ancoraggio.  
  
-   Gestione di un elenco di tutti i documenti attualmente aperti in una tabella documenti in esecuzione (RDT) per coordinare la persistenza dei documenti e per garantire che un documento non è possibile aprire in più modo o in modi non compatibili.  
  
-   Supporto di interfaccia di routing di comandi e la gestione dei comandi, `IOleCommandTarget`.  
  
-   Caricamento di pacchetti VSPackage in momenti appropriati. Caricamento ritardato un pacchetto VSPackage è necessario migliorare le prestazioni della shell.  
  
-   Gestione di determinati servizi, condivisi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, che fornisce la funzionalità shell di base, e <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, che fornisce funzionalità di windowing di base.  
  
-   Gestione dei file di soluzione (sln). Le soluzioni contengono gruppi di progetti correlati, simili ai file dell'area di lavoro (con estensione DSW) in Visual C++ 6.0.  
  
-   Selezione di shell a livello di rilevamento, il contesto e valuta. La shell rileva i tipi seguenti di elementi:  
  
    -   Il progetto corrente  
  
    -   L'elemento del progetto corrente o l'ID dell'elemento corrente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   La selezione corrente per il **proprietà** finestra o `SelectionContainer`  
  
    -   Contesto dell'interfaccia utente, ID o CmdUIGuids che consentono di controllare la visibilità dei comandi, menu e barre degli strumenti  
  
    -   Gli elementi attualmente attivi, ad esempio la finestra attiva, documento e gestione degli annullamenti  
  
    -   Gli attributi di contesto dell'utente che determinano Guida dinamica  
  
 La shell consente di eseguire anche la comunicazione tra i servizi correnti e installati i pacchetti VSPackage. Supporta le funzionalità principali della shell e li rende disponibili per tutti i pacchetti VSPackage integrati [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Queste funzionalità di base includono gli elementi seguenti:  
  
-   **Sulle** della finestra di dialogo e nella schermata iniziale  
  
-   **Aggiungere nuovo e Aggiungi elemento esistente** finestre di dialogo  
  
-   **Visualizzazione classi** finestra e **Visualizzatore oggetti**  
  
-   **I riferimenti** nella finestra di dialogo  
  
-   **Struttura documento** finestra  
  
-   **Guida dinamica** finestra  
  
-   **Trovare** e **sostituire**  
  
-   **Apri progetto** e **Apri File** finestre di dialogo nel **New** menu  
  
-   **Le opzioni** nella finestra di dialogo di **strumenti** menu  
  
-   Finestra **Proprietà**  
  
-   **Esplora soluzioni**  
  
-   **Elenco delle attività** finestra  
  
-   **Casella degli strumenti**  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
