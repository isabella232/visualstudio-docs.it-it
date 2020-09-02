---
title: Estensione dell'editor e dei servizi di linguaggio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 085e1b5c1fbfbbaf5649966738f2864e0b72ed35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674777"
---
# <a name="extending-the-editor-and-language-services"></a>Estensione dell'editor e dei servizi di linguaggio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiungere le funzionalità del servizio di linguaggio (ad esempio IntelliSense) al proprio editor ed estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio.  Per un elenco completo degli elementi che è possibile estendere, vedere i [punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 È possibile estendere la maggior parte delle funzionalità dell'editor usando il Managed Extensibility Framework (MEF). Se, ad esempio, la funzionalità dell'editor che si desidera estendere è la colorazione della sintassi, è possibile scrivere una *parte del componente* MEF che definisce le classificazioni per le quali si desidera la colorazione e il modo in cui si desidera gestirle. L'editor supporta inoltre più estensioni della stessa funzionalità.  
  
 Il livello di presentazione dell'editor è basato su Windows Presentation Framework (WPF). WPF fornisce una libreria di grafica per la formattazione flessibile del testo e fornisce anche visualizzazioni quali grafica e animazioni.  
  
 Visual Studio SDK fornisce adattatori noti come *shim* per supportare i pacchetti VSPackage scritti per le versioni precedenti. Tuttavia, se si dispone di un pacchetto VSPackage esistente, è consigliabile aggiornarlo alla nuova tecnologia per ottenere prestazioni e affidabilità migliori.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Introduzione alle estensioni dell'editor e dei servizi di linguaggio](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Viene illustrato come creare un'estensione per l'editor.|  
|[Componenti e funzionalità dell'editor](../extensibility/inside-the-editor.md)|Viene descritta la struttura generale dell'editor ed elencate alcune delle relative funzionalità.|  
|[Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Viene illustrato come utilizzare il Managed Extensibility Framework (MEF) con l'editor.|  
|[Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)|Elenca i punti di estensione dell'editor. I punti di estensione rappresentano le funzionalità dell'editor che possono essere estese.|  
|[Procedura dettagliata: Creazione di un'area di controllo di visualizzazione, di comandi e impostazioni (guide di colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Viene illustrata la compilazione di un'area di visualizzazione della vista che disegna linee gudie di colonna per facilitare la conservazione del codice a una determinata larghezza di visualizzazione.  Mostra anche le impostazioni di lettura e scrittura, nonché la dichiarazione e l'implementazione di comandi che è possibile richiamare dalla finestra di comando.|  
|[Importazioni dell'editor](../extensibility/editor-imports.md)|Elenca i servizi che possono essere importati da un'estensione.|  
|[Adattamento del codice legacy all'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Vengono illustrati diversi modi per adattare il codice legacy (precedente a Visual Studio 2010) per estendere l'editor.|  
|[Migrazione di un servizio di linguaggio legacy](../extensibility/internals/migrating-a-legacy-language-service.md)|Viene illustrato come eseguire la migrazione di un servizio di linguaggio basato su VSPackage.|  
|[Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Mostra come collegare un tipo di contenuto a un'estensione di file.|  
|[Procedura dettagliata: Creazione di un glifo di margine](../extensibility/walkthrough-creating-a-margin-glyph.md)|Viene illustrato come aggiungere un'icona a un margine.|  
|[Procedura dettagliata: Evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md)|Mostra come usare i *tag* per evidenziare il testo.|  
|[Procedura dettagliata: Definizione della struttura](../extensibility/walkthrough-outlining.md)|Viene illustrato come aggiungere la struttura per tipi di parentesi graffe specifici.|  
|[Procedura dettagliata: Visualizzazione della corrispondenza parentesi graffe](../extensibility/walkthrough-displaying-matching-braces.md)|Viene illustrato come evidenziare le parentesi graffe corrispondenti.|  
|[Procedura dettagliata: Visualizzazione delle informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Viene illustrato come visualizzare i popup informazioni rapide che descrivono elementi di codice, ad esempio proprietà, metodi ed eventi.|  
|[Procedura dettagliata: Visualizzazione della funzionalità di supporto alla firma](../extensibility/walkthrough-displaying-signature-help.md)|Viene illustrato come visualizzare i popup che forniscono informazioni sul numero e sui tipi di parametri in una firma.|  
|[Procedura dettagliata: Visualizzazione del completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)|Viene illustrato come implementare il completamento delle istruzioni.|  
|[Procedura dettagliata: Implementazione di frammenti di codice](../extensibility/walkthrough-implementing-code-snippets.md)|Viene illustrato come implementare l'espansione del frammento di codice.|  
|[Procedura dettagliata: Visualizzazione dei suggerimenti delle icone lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Mostra come visualizzare le lampadine per i suggerimenti del codice.|  
|[Procedura dettagliata: Uso di un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Mostra come associare un comando di menu in un VSPackage a un componente MEF.|  
|[Procedura dettagliata: Uso di una combinazione di tasti con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Mostra come associare un collegamento di menu in un VSPackage con un componente MEF.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Fornisce informazioni sul Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Fornisce informazioni sul Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Informazioni di riferimento  
 L'editor di Visual Studio include gli spazi dei nomi seguenti.  
  
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
