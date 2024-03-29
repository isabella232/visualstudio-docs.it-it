---
title: Estensione dell'editor e dei servizi di linguaggio | Microsoft Docs
description: È possibile aggiungere funzionalità del servizio di linguaggio a un editor ed estendere le funzionalità dell Visual Studio editor di codice. Informazioni sul Managed Extensibility Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8fa21afe5bffa298847aa90229e087c94b38f8a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125127"
---
# <a name="extend-the-editor-and-language-services"></a>Estendere l'editor e i servizi di linguaggio
È possibile aggiungere funzionalità del servizio di linguaggio ( ad esempio IntelliSense) al proprio editor ed estendere la maggior parte delle funzionalità dell Visual Studio editor di codice.  Per un elenco completo degli elementi che è possibile estendere, vedere Punti di estensione del servizio [di linguaggio e dell'editor.](../extensibility/language-service-and-editor-extension-points.md)

 È possibile estendere la maggior parte delle funzionalità dell'editor usando Managed Extensibility Framework (MEF). Ad esempio, se la funzionalità dell'editor che si vuole estendere è la colorazione della sintassi, è possibile scrivere una parte del componente *MEF* che definisce le classificazioni per le quali si vuole una colorazione diversa e come si vuole gestirle. L'editor supporta anche più estensioni della stessa funzionalità.

 Il livello di presentazione dell'editor è basato Windows Presentation Framework (WPF). WPF offre una libreria grafica per la formattazione del testo flessibile e anche visualizzazioni come grafica e animazioni.

 L Visual Studio SDK fornisce adattatori noti come *s shims* per supportare i pacchetti VSPackage scritti per le versioni precedenti. Tuttavia, se si dispone di un VSPackage esistente, è consigliabile aggiornarlo alla nuova tecnologia per ottenere prestazioni e affidabilità migliori.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Introduzione alle estensioni del servizio di linguaggio e dell'editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Viene illustrato come creare un'estensione per l'editor.|
|[All'interno dell'editor](../extensibility/inside-the-editor.md)|Viene descritta la struttura generale dell'editor e ne vengono elencate alcune funzionalità.|
|[Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Viene illustrato come usare il Managed Extensibility Framework (MEF) con l'editor.|
|[Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)|Elenca i punti di estensione dell'editor. I punti di estensione rappresentano le funzionalità dell'editor che possono essere estese.|
|[Procedura dettagliata: Creare un'area di controllo della visualizzazione, comandi e impostazioni (guide di colonna)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Illustra in dettaglio e illustra la creazione di un'area di controllo della visualizzazione che disegna linee guida di colonna per mantenere il codice fino a una determinata larghezza di visualizzazione.  Mostra anche le impostazioni di lettura e scrittura, nonché la dichiarazione e l'implementazione di comandi che è possibile richiamare dalla finestra di comando.|
|[Importazioni dell'editor](../extensibility/editor-imports.md)|Elenca i servizi che un'estensione può importare.|
|[Adattare il codice legacy all'editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/adapting-legacy-code-to-the-editor?preserve-view=true&view=vs-2015)|Illustra diversi modi per adattare il codice legacy (versione Visual Studio 2010) per estendere l'editor.|
|[Eseguire la migrazione di un servizio di linguaggio legacy](../extensibility/internals/migrating-a-legacy-language-service.md)|Viene illustrato come eseguire la migrazione di un servizio di linguaggio basato su VSPackage.|
|[Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Illustra come collegare un tipo di contenuto a un'estensione di file.|
|[Procedura dettagliata: Creare un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md)|Illustra come aggiungere un'icona a un margine.|
|[Procedura dettagliata: Evidenziare il testo](../extensibility/walkthrough-highlighting-text.md)|Illustra come usare i *tag per* evidenziare il testo.|
|[Procedura dettagliata: Aggiungere la struttura](../extensibility/walkthrough-outlining.md)|Illustra come aggiungere la struttura per tipi specifici di parentesi graffe.|
|[Procedura dettagliata: Visualizzare le parentesi graffe corrispondenti](../extensibility/walkthrough-displaying-matching-braces.md)|Illustra come evidenziare le parentesi graffe corrispondenti.|
|[Procedura dettagliata: Visualizzare le descrizioni comando di Informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Illustra come visualizzare popup di informazioni rapide che descrivono elementi di codice, ad esempio proprietà, metodi ed eventi.|
|[Procedura dettagliata: Visualizzare la Guida alla firma](../extensibility/walkthrough-displaying-signature-help.md)|Viene illustrato come visualizzare popup che forniscono informazioni sul numero e sui tipi di parametri in una firma.|
|[Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)|Viene illustrato come implementare il completamento delle istruzioni.|
|[Procedura dettagliata: Implementare frammenti di codice](../extensibility/walkthrough-implementing-code-snippets.md)|Illustra come implementare l'espansione del frammento di codice.|
|[Procedura dettagliata: Visualizzare i suggerimenti per le lampadine](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Illustra come visualizzare le lampadine per i suggerimenti del codice.|
|[Procedura dettagliata: Usare un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Illustra come associare un comando di menu in un VSPackage a un componente MEF.|
|[Procedura dettagliata: Usare un tasto di scelta rapida con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Illustra come associare un collegamento di menu in un VSPackage a un componente MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Fornisce informazioni sul Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Fornisce informazioni sul Windows Presentation Foundation (WPF).|

## <a name="reference"></a>Riferimento
 L Visual Studio editor include gli spazi dei nomi seguenti.

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