---
title: Estensione dell'editor e dei servizi di linguaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321bd82eb83ef37dc3981e38cc23d1d4b5685802
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2020
ms.locfileid: "93413944"
---
# <a name="extend-the-editor-and-language-services"></a>Estendere l'editor e i servizi di linguaggio
È possibile aggiungere le funzionalità del servizio di linguaggio (ad esempio IntelliSense) al proprio editor ed estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio.  Per un elenco completo degli elementi che è possibile estendere, vedere i [punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md).

 È possibile estendere la maggior parte delle funzionalità dell'editor usando il Managed Extensibility Framework (MEF). Se, ad esempio, la funzionalità dell'editor che si desidera estendere è la colorazione della sintassi, è possibile scrivere una *parte del componente* MEF che definisce le classificazioni per le quali si desidera la colorazione e il modo in cui si desidera gestirle. L'editor supporta inoltre più estensioni della stessa funzionalità.

 Il livello di presentazione dell'editor è basato su Windows Presentation Framework (WPF). WPF fornisce una libreria di grafica per la formattazione flessibile del testo e fornisce anche visualizzazioni quali grafica e animazioni.

 Visual Studio SDK fornisce adattatori noti come *shim* per supportare i pacchetti VSPackage scritti per le versioni precedenti. Tuttavia, se si dispone di un pacchetto VSPackage esistente, è consigliabile aggiornarlo alla nuova tecnologia per ottenere prestazioni e affidabilità migliori.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Introduzione alle estensioni dell'editor e dei servizi di linguaggio](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Viene illustrato come creare un'estensione per l'editor.|
|[All'interno dell'editor](../extensibility/inside-the-editor.md)|Viene descritta la struttura generale dell'editor ed elencate alcune delle relative funzionalità.|
|[Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Viene illustrato come utilizzare il Managed Extensibility Framework (MEF) con l'editor.|
|[Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)|Elenca i punti di estensione dell'editor. I punti di estensione rappresentano le funzionalità dell'editor che possono essere estese.|
|[Procedura dettagliata: creare un'area di visualizzazione, comandi e impostazioni (guide di colonna)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Viene illustrata la creazione di un'area di visualizzazione della vista che disegna linee guida di colonna per facilitare la conservazione del codice a una determinata larghezza di visualizzazione.  Mostra anche le impostazioni di lettura e scrittura, nonché la dichiarazione e l'implementazione di comandi che è possibile richiamare dalla finestra di comando.|
|[Importazioni editor](../extensibility/editor-imports.md)|Elenca i servizi che possono essere importati da un'estensione.|
|[Adattare il codice legacy all'editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/adapting-legacy-code-to-the-editor?preserve-view=true&view=vs-2015)|Vengono illustrati diversi modi per adattare il codice legacy (precedente a Visual Studio 2010) per estendere l'editor.|
|[Eseguire la migrazione di un servizio di linguaggio legacy](../extensibility/internals/migrating-a-legacy-language-service.md)|Viene illustrato come eseguire la migrazione di un servizio di linguaggio basato su VSPackage.|
|[Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Mostra come collegare un tipo di contenuto a un'estensione di file.|
|[Procedura dettagliata: creare un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md)|Viene illustrato come aggiungere un'icona a un margine.|
|[Procedura dettagliata: evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md)|Mostra come usare i *tag* per evidenziare il testo.|
|[Procedura dettagliata: aggiungere la struttura](../extensibility/walkthrough-outlining.md)|Viene illustrato come aggiungere la struttura per tipi di parentesi graffe specifici.|
|[Procedura dettagliata: visualizzare le parentesi graffe corrispondenti](../extensibility/walkthrough-displaying-matching-braces.md)|Viene illustrato come evidenziare le parentesi graffe corrispondenti.|
|[Procedura dettagliata: visualizzare le descrizioni comandi di informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Viene illustrato come visualizzare i popup informazioni rapide che descrivono elementi di codice, ad esempio proprietà, metodi ed eventi.|
|[Procedura dettagliata: visualizzare la guida per la firma](../extensibility/walkthrough-displaying-signature-help.md)|Viene illustrato come visualizzare i popup che forniscono informazioni sul numero e sui tipi di parametri in una firma.|
|[Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)|Viene illustrato come implementare il completamento delle istruzioni.|
|[Procedura dettagliata: implementare frammenti di codice](../extensibility/walkthrough-implementing-code-snippets.md)|Viene illustrato come implementare l'espansione del frammento di codice.|
|[Procedura dettagliata: visualizzare i suggerimenti della lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Mostra come visualizzare le lampadine per i suggerimenti del codice.|
|[Procedura dettagliata: usare un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Mostra come associare un comando di menu in un VSPackage a un componente MEF.|
|[Procedura dettagliata: usare un tasto di scelta rapida con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Mostra come associare un collegamento di menu in un VSPackage con un componente MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Fornisce informazioni sul Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Fornisce informazioni sul Windows Presentation Foundation (WPF).|

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