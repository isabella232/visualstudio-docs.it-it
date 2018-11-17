---
title: Estensione dell'Editor e servizi di linguaggio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91eab151680d936c350c8c5745aec6c9fe86e47c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723061"
---
# <a name="extending-the-editor-and-language-services"></a>Estensione dell'editor e dei servizi di linguaggio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiungere funzionalità del servizio linguaggio (ad esempio IntelliSense) per il proprio editor ed estendere la maggior parte delle funzionalità dell'editor del codice di Visual Studio.  Per un elenco completo di ciò che è possibile estendere, vedere [servizio di linguaggio e punti di estensione Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Si estende la maggior parte delle funzionalità dell'editor mediante Managed Extensibility Framework (MEF). Ad esempio, se si vuole estendere la funzionalità di editor è la colorazione della sintassi, è possibile scrivere un MEF *parte del componente* che consente di definire le classificazioni per cui si desidera colori diversi e voluti gestita. L'editor supporta anche più estensioni della funzionalità stessa.  
  
 Il livello di presentazione dell'editor è basato su Windows Presentation Framework (WPF). WPF fornisce una libreria grafica per la formattazione del testo flessibile e offre anche viste, ad esempio immagini e animazioni.  
  
 Visual Studio SDK fornisce adapter detto *shim* per supportare i pacchetti VSPackage che sono state scritte per versioni precedenti. Tuttavia, se si dispone di un pacchetto VSPackage esistente, è consigliabile aggiornarla per la nuova tecnologia per ottenere affidabilità e prestazioni migliori.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Introduzione alle estensioni dell'editor e dei servizi di linguaggio](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Viene illustrato come creare un'estensione per l'editor.|  
|[Componenti e funzionalità dell'editor](../extensibility/inside-the-editor.md)|Descrive la struttura generale dell'editor e sono elencate alcune delle relative funzionalità.|  
|[Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Illustra come usare Managed Extensibility Framework (MEF) con l'editor.|  
|[Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)|Elenca i punti di estensione dell'editor. Punti di estensione rappresentano le funzionalità dell'editor che possono essere estesa.|  
|[Procedura dettagliata: Creazione di un'area di controllo di visualizzazione, di comandi e impostazioni (guide di colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Descrive e illustra la creazione di un'area di controllo di visualizzazione che consente di disegnare linee gudie colonna che consentono di mantenere il codice per una determinata larghezza di visualizzazione.  Mostra anche la lettura e scrittura delle impostazioni, nonché la dichiarazione e implementazione di comandi che è possibile richiamare dalla finestra di comando.|  
|[Importazioni dell'editor](../extensibility/editor-imports.md)|Elenca i servizi che è possibile importare un'estensione.|  
|[Adattamento del codice legacy all'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Illustra modi diversi per adattare il codice legacy (precedenti a Visual Studio 2010) per estendere l'editor.|  
|[Migrazione di un servizio di linguaggio Legacy](../extensibility/internals/migrating-a-legacy-language-service.md)|Viene illustrato come eseguire la migrazione di un servizio di linguaggio basato su VSPackage.|  
|[Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Illustra come collegare un tipo di contenuto a un'estensione di file.|  
|[Procedura dettagliata: Creazione di un glifo di margine](../extensibility/walkthrough-creating-a-margin-glyph.md)|Viene illustrato come aggiungere un'icona a margine.|  
|[Procedura dettagliata: Evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md)|Viene illustrato come utilizzare *tag* per evidenziare il testo.|  
|[Procedura dettagliata: Definizione della struttura](../extensibility/walkthrough-outlining.md)|Viene illustrato come aggiungere la struttura per tipi specifici di parentesi graffe.|  
|[Procedura dettagliata: Visualizzazione della corrispondenza parentesi graffe](../extensibility/walkthrough-displaying-matching-braces.md)|Viene illustrato come evidenziare le parentesi graffe corrispondenti.|  
|[Procedura dettagliata: Visualizzazione delle informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Viene illustrato come visualizzare i popup informazioni rapide che descrivono gli elementi di codice, ad esempio proprietà, metodi ed eventi.|  
|[Procedura dettagliata: Visualizzazione della funzionalità di supporto alla firma](../extensibility/walkthrough-displaying-signature-help.md)|Viene illustrato come visualizzare i popup che forniscono informazioni relative a numero e tipi di parametri in una firma.|  
|[Procedura dettagliata: Visualizzazione del completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)|Viene illustrato come implementare il completamento delle istruzioni.|  
|[Procedura dettagliata: Implementazione di frammenti di codice](../extensibility/walkthrough-implementing-code-snippets.md)|Viene illustrato come implementare l'espansione del frammento di codice.|  
|[Procedura dettagliata: Visualizzazione dei suggerimenti delle icone lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Viene illustrato come visualizzare le lampadine per i suggerimenti di codice.|  
|[Procedura dettagliata: Uso di un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Viene illustrato come associare un comando di menu in un pacchetto VSPackage a un componente MEF.|  
|[Procedura dettagliata: Uso di una combinazione di tasti con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Viene illustrato come associare un collegamento di menu in un pacchetto VSPackage a un componente MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Vengono fornite informazioni su Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Vengono fornite informazioni su Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Riferimenti  
 L'editor di Visual Studio include spazi dei nomi seguenti.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>

