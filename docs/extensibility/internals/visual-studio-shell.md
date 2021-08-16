---
title: Visual Studio Shell | Microsoft Docs
description: La shell Visual Studio è l'agente principale di integrazione in Visual Studio e fornisce funzionalità di base e supporta la comunicazione incrociata tra pacchetti VSPackage.
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
ms.openlocfilehash: 0d2d79a36acdc7c210b81b5215d242d95adb947e8dcf17aec23a62bf4e05708a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375429"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell è l'agente principale di integrazione in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . La shell fornisce le funzionalità necessarie per consentire ai pacchetti VSPackage di condividere servizi comuni. Poiché l'obiettivo dell'architettura di è quello di inserire le funzionalità principali nei pacchetti VSPackage, la shell è un framework per fornire funzionalità di base e supportare la comunicazione incrociata tra i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetti VSPackage componenti.

## <a name="shell-responsibilities"></a>Responsabilità della shell
 La shell ha le responsabilità principali seguenti:

- Supporto di elementi di base dell'interfaccia utente (tramite interfacce COM). Sono inclusi i menu e le barre degli strumenti predefiniti, le cornice della finestra del documento o le finestre figlio dell'interfaccia a documenti multipli e le finestre degli strumenti e il supporto dell'ancoraggio.

- Gestione di un elenco in esecuzione di tutti i documenti attualmente aperti in una tabella di documenti in esecuzione (RDT) per coordinare la persistenza dei documenti e garantire che un documento non possa essere aperto in più di un modo o in modi incompatibili.

- Supporto dell'interfaccia di routing dei comandi e di gestione dei comandi, `IOleCommandTarget` .

- Caricamento di pacchetti VSPackage nei momenti appropriati. Il caricamento ritardato di un pacchetto VSPackage è necessario per migliorare le prestazioni della shell.

- Gestione di alcuni servizi condivisi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> , che fornisce funzionalità di base della shell, e , che fornisce funzionalità di <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> windowing di base.

- Gestione dei file di soluzione (con estensione sln). Le soluzioni contengono gruppi di progetti correlati, simili ai file dell'area di lavoro (con estensione dsw) in Visual C++ 6.0.

- Rilevamento della selezione, del contesto e della valuta a livello di shell. La shell tiene traccia dei tipi di elementi seguenti:

  - Progetto corrente

  - Elemento di progetto corrente o ItemID corrente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Selezione corrente per la **finestra** Proprietà o `SelectionContainer`

  - ID di contesto dell'interfaccia utente o CmdUIGuid che controllano la visibilità di comandi, menu e barre degli strumenti

  - Elementi attualmente attivi, ad esempio la finestra attiva, il documento e il gestore di annullamento

  - Attributi del contesto utente che guidano la Guida dinamica

  La shell media anche la comunicazione tra i pacchetti VSPackage installati e i servizi correnti. Supporta le funzionalità di base della shell e le rende disponibili per tutti i PACCHETTI VSPackage integrati in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Queste funzionalità di base includono gli elementi seguenti:

- **Finestra di** dialogo Informazioni su e schermata iniziale

- **Finestre di dialogo Aggiungi nuovo elemento e Aggiungi elemento** esistente

- **Visualizzazione classi** e **Visualizzatore oggetti**

- **Finestra di** dialogo Riferimenti

- **Finestra Struttura documento**

- **Finestra Guida** dinamica

- **Trova** e **sostituisci**

- **Aprire Project** e **apri file** nel **menu** Nuovo

- **Finestra** di dialogo Opzioni **del** menu Strumenti

- **Finestra** Proprietà

- **Esplora soluzioni**

- **Elenco attività** finestra

- **Casella degli strumenti**

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
