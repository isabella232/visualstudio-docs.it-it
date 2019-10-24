---
title: Shell di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60aa48da701857508f9b6fd7fc3d9d0c0603046e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722048"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell è l'agente primario di integrazione in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. La shell fornisce la funzionalità necessaria per consentire ai pacchetti VSPackage di condividere i servizi comuni. Poiché l'obiettivo dell'architettura di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è quello di sfruttare le funzionalità principali nei pacchetti VSPackage, la shell è un Framework per fornire funzionalità di base e supportare la comunicazione incrociata tra i pacchetti VSPackage dei componenti.

## <a name="shell-responsibilities"></a>Responsabilità della shell
 La shell ha le responsabilità principali seguenti:

- Supporto (tramite interfacce COM) elementi di base dell'interfaccia utente (UI). Sono inclusi i menu e le barre degli strumenti predefiniti, le cornici della finestra del documento o le finestre figlio MDI, i frame della finestra degli strumenti e il supporto per l'ancoraggio.

- Gestione di un elenco in esecuzione di tutti i documenti attualmente aperti in una tabella documenti in esecuzione (RDT) per coordinare la persistenza dei documenti e garantire che un documento non possa essere aperto in più di un modo o in modi incompatibili.

- Supporto del routing di comandi e dell'interfaccia di gestione dei comandi, `IOleCommandTarget`.

- Caricamento dei pacchetti VSPackage in momenti appropriati. Il caricamento ritardato di un pacchetto VSPackage è necessario per migliorare le prestazioni della shell.

- Gestione di determinati servizi condivisi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, che fornisce funzionalità di base della shell e <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, che fornisce funzionalità di base per la finestra.

- Gestione dei file di soluzione (con estensione sln). Le soluzioni contengono gruppi di progetti correlati, simili ai file dell'area di lavoro (con C++ estensione DSW) in Visual 6,0.

- Rilevamento di selezione, contesto e valuta a livello di Shell. La shell tiene traccia dei seguenti tipi di elementi:

  - Il progetto corrente

  - Elemento del progetto corrente o ItemID <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> corrente

  - Selezione corrente per la finestra **Proprietà** o `SelectionContainer`

  - ID del contesto dell'interfaccia utente o CmdUIGuids che controllano la visibilità di comandi, menu e barre degli strumenti

  - Elementi attualmente attivi, ad esempio la finestra attiva, il documento e il gestore di annullamento

  - Attributi del contesto utente che guidano la Guida dinamica

  La shell media inoltre la comunicazione tra i pacchetti VSPackage installati e i servizi correnti. Supporta le funzionalità principali della shell e le rende disponibili per tutti i pacchetti VSPackage integrati in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Queste funzionalità principali includono gli elementi seguenti:

- Finestra **di dialogo informazioni su** e schermata iniziale

- Finestra **di dialogo Aggiungi nuovo elemento e Aggiungi elemento esistente**

- Finestra **Visualizzazione classi** e **Visualizzatore oggetti**

- Finestra di dialogo **riferimenti**

- Finestra **struttura documento**

- Finestra **Guida dinamica**

- **Trova** e **Sostituisci**

- **Aprire il progetto** e aprire le finestre di dialogo **file** dal menu **nuovo**

- Finestra di dialogo **Opzioni** del menu **strumenti**

- Finestra **Proprietà**

- **Esplora soluzioni**

- Finestra **elenco attività**

- **Casella degli strumenti**

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)