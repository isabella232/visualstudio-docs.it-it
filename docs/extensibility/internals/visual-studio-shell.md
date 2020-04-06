---
title: Visual Studio Shell - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704008"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell è l'agente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]principale dell'integrazione in . La shell fornisce le funzionalità necessarie per consentire a VSPackage di condividere servizi comuni. Poiché l'obiettivo dell'architettura di è quello di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vestire la funzionalità principale nei vsPackage, la shell è un framework per fornire funzionalità di base e supportare la comunicazione incrociata tra i relativi componenti VSPackage.

## <a name="shell-responsibilities"></a>Responsabilità della Shell
 La shell ha le seguenti responsabilità chiave:

- Supporto (tramite interfacce COM) elementi di base dell'interfaccia utente (UI). Questi includono menu e barre degli strumenti predefinite, cornici di finestre di documento o finestre figlio di interfaccia a documenti multielemento (MDI), e cornici di finestre degli strumenti e supporto di ancoraggio.

- Gestione di un elenco in esecuzione di tutti i documenti attualmente aperti in una tabella documenti in esecuzione (RDT) per coordinare la persistenza dei documenti e garantire che un documento non possa essere aperto in più modi o in modi incompatibili.

- Supporto dell'interfaccia di routing dei `IOleCommandTarget`comandi e di gestione dei comandi, .

- Caricamento di pacchetti VSPackage nei momenti appropriati. Ritardare il caricamento di un VSPackage è necessario per migliorare le prestazioni della shell.

- Gestione di determinati servizi <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>condivisi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, che fornisce funzionalità di base della shell e , che fornisce funzionalità di base per la finestratura.

- Gestione dei file di soluzione (sln). Le soluzioni contengono gruppi di progetti correlati, in modo simile ai file dell'area di lavoro (con estensione dsw) in Visual C .NET 6.0.

- Rilevamento della selezione, del contesto e della valuta a livello di shell. La shell tiene traccia dei seguenti tipi di elementi:

  - Il progetto in corso

  - L'elemento di progetto corrente o ItemID l'oggetto corrente<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - La selezione corrente per la finestra **Proprietà** o`SelectionContainer`

  - ID di contesto dell'interfaccia utente o CmdUIChe controlla la visibilità di comandi, menu e barre degli strumenti

  - Gli elementi attualmente attivi, ad esempio la finestra attiva, il documento e il gestore di annullamento

  - Attributi del contesto utente che guidano la Guida dinamica

  La shell media anche la comunicazione tra i package VS installati e i servizi correnti. Supporta le funzionalità di base della shell e le rende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]disponibili per tutti i package VS integrati in . Queste funzionalità principali includono i seguenti elementi:

- **Finestra di** dialogo e schermata iniziale

- Finestre di dialogo **Aggiungi nuovo e Aggiungi elemento esistente**

- **Finestra Visualizzazione classi** e **Visualizzatore oggetti**

- **Finestra di** dialogo Riferimenti

- **Finestra Struttura documento**

- **Finestra Guida dinamica**

- **Trova** e **sostituisci**

- **Aprire** le finestre di dialogo Progetto e **Apri file** nel menu **Nuovo**

- **Finestra** di dialogo Opzioni del menu **Strumenti**

- **Finestra Proprietà**

- **Esplora soluzioni**

- **Finestra Elenco attività**

- **Casella degli strumenti**

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
