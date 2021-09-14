---
title: Visual Studio Shell | Microsoft Docs
description: La Visual Studio shell è l'agente principale di integrazione in Visual Studio e fornisce funzionalità di base e supporta la comunicazione incrociata tra vspackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7f57defce4eb9b46185f0d266822b5f4a0d2e719
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627269"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell è l'agente primario di integrazione in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . La shell fornisce le funzionalità necessarie per consentire ai pacchetti VSPackage di condividere i servizi comuni. Poiché l'obiettivo dell'architettura di è la funzionalità principale dei pacchetti VSPackage, la shell è un framework per fornire funzionalità di base e supportare la comunicazione incrociata tra i pacchetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage del componente.

## <a name="shell-responsibilities"></a>Responsabilità della shell
 La shell ha le responsabilità principali seguenti:

- Supporto (tramite interfacce COM) elementi di base dell'interfaccia utente. Sono inclusi menu e barre degli strumenti predefiniti, finestre della finestra del documento o finestre figlio MDI (Multi-Document Interface) e finestre degli strumenti e supporto di ancoraggio.

- Gestione di un elenco in esecuzione di tutti i documenti attualmente aperti in una tabella di documenti in esecuzione (RDT) per coordinare la persistenza dei documenti e garantire che un documento non possa essere aperto in più modi o in modo incompatibile.

- Supporto dell'interfaccia di routing dei comandi e di gestione dei comandi, `IOleCommandTarget` .

- Caricamento di VSPackage nei momenti appropriati. Il caricamento ritardato di un VSPackage è necessario per migliorare le prestazioni della shell.

- Gestione di alcuni servizi condivisi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> , che fornisce funzionalità shell di base e , che fornisce funzionalità di finestra di <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> base.

- Gestione dei file di soluzione (sln). Le soluzioni contengono gruppi di progetti correlati, simili ai file dell'area di lavoro (con estensione dsw) in Visual C++ 6.0.

- Rilevamento della selezione, del contesto e della valuta a livello di shell. La shell tiene traccia dei tipi di elementi seguenti:

  - Progetto corrente

  - Elemento di progetto corrente o ItemID corrente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Selezione corrente per la **finestra Proprietà** o `SelectionContainer`

  - ID di contesto dell'interfaccia utente o CmdUIGuid che controllano la visibilità di comandi, menu e barre degli strumenti

  - Elementi attualmente attivi, ad esempio la finestra attiva, il documento e il gestore di annullamento

  - Attributi del contesto utente che guidano la Guida dinamica

  La shell media anche la comunicazione tra i pacchetti VSPackage installati e i servizi correnti. Supporta le funzionalità principali della shell e le rende disponibili per tutti i pacchetti VSPackage integrati in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Queste funzionalità principali includono gli elementi seguenti:

- **Informazioni sulla** finestra di dialogo e sulla schermata iniziale

- **Finestre di dialogo Aggiungi nuovo elemento e Aggiungi elemento** esistente

- **Visualizzazione classi** finestra e **Visualizzatore oggetti**

- **Finestra di** dialogo Riferimenti

- **Finestra Struttura** documento

- **Finestra Guida** dinamica

- **Trovare** e **sostituire**

- **Aprire Project** finestre **di dialogo Apri file** nel menu Nuovo 

- **Finestra** di dialogo Opzioni **del** menu Strumenti

- **Finestra Proprietà**

- **Esplora soluzioni**

- **Elenco attività** finestra

- **Casella degli strumenti**

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
