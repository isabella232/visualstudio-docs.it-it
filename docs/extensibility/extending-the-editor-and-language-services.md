---
title: Estensione dell'editor e dei servizi di linguaggio . Documenti Microsoft
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
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711706"
---
# <a name="extend-the-editor-and-language-services"></a>Estendere l'editor e i servizi di linguaggioExtend the editor and language services
È possibile aggiungere funzionalità del servizio di linguaggio (ad esempio IntelliSense) al proprio editor ed estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio.You can add language service features (such as IntelliSense) to your own editor, and extend most features of the Visual Studio code editor.  Per un elenco completo degli elementi che è possibile estendere, vedere Servizio di linguaggio e punti di [estensione dell'editor](../extensibility/language-service-and-editor-extension-points.md).

 Estendere la maggior parte delle funzionalità dell'editor utilizzando Managed Extensibility Framework (MEF). Ad esempio, se la funzionalità editor che si desidera estendere è la colorazione della sintassi, è possibile scrivere una *parte componente* MEF che definisce le classificazioni per le quali si desidera una colorazione diversa e il modo in cui si desidera gestirle. L'editor supporta anche più estensioni della stessa funzionalità.

 Il livello di presentazione dell'editor è basato su Windows Presentation Framework (WPF). WPFWPF fornisce una libreria grafica per la formattazione del testo flessibile e fornisce anche visualizzazioni quali grafica e animazioni.

 Visual Studio SDK fornisce adattatori noti come *shim* per supportare i pacchetti VSPackage scritti per le versioni precedenti. Tuttavia, se si dispone di un VSPackage esistente, si consiglia di aggiornarlo alla nuova tecnologia per ottenere prestazioni e affidabilità migliori.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Introduzione al servizio di linguaggio e alle estensioni dell'editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Viene illustrato come creare un'estensione per l'editor.|
|[All'interno dell'editor](../extensibility/inside-the-editor.md)|Descrive la struttura generale dell'editor ed elenca alcune delle relative funzionalità.|
|[Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Viene illustrato come utilizzare Managed Extensibility Framework (MEF) con l'editor.|
|[Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)|Elenca i punti di estensione dell'editor. I punti di estensione rappresentano le funzionalità dell'editor che possono essere estese.|
|[Procedura dettagliata: Creare un'area di controllo, comandi e impostazioni di visualizzazione (guide colonne)Walkthrough: Create a view adornment, commands, and settings (column guides)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Illustra e illustra la creazione di un'area di controllo della visualizzazione che disegna linee guida delle colonne per mantenere il codice a una determinata larghezza di visualizzazione.  Vengono inoltre illustrate le impostazioni di lettura e scrittura, nonché la dichiarazione e l'implementazione di comandi che è possibile richiamare dalla finestra di comando.|
|[Importazioni dell'editor](../extensibility/editor-imports.md)|Elenca i servizi che un'estensione può importare.|
|[Adattare il codice legacy all'editor](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Vengono illustrati diversi modi per adattare il codice legacy (pre-Visual Studio 2010) per estendere l'editor.|
|[Eseguire la migrazione di un servizio di linguaggio legacyMigrate a legacy language service](../extensibility/internals/migrating-a-legacy-language-service.md)|Viene illustrato come eseguire la migrazione di un servizio di linguaggio basato su VSPackage.Explains how to migrate a VSPackage based language service.|
|[Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Viene illustrato come collegare un tipo di contenuto a un'estensione di file.|
|[Procedura dettagliata: Creare un glifo di margineWalkthrough: Create a margin glyph](../extensibility/walkthrough-creating-a-margin-glyph.md)|Viene illustrato come aggiungere un'icona a un margine.|
|[Procedura dettagliata: Evidenziare il testoWalkthrough: Highlight text](../extensibility/walkthrough-highlighting-text.md)|Viene illustrato come utilizzare *i tag* per evidenziare il testo.|
|[Procedura dettagliata: Aggiungere la strutturaWalkthrough: Add outlining](../extensibility/walkthrough-outlining.md)|Viene illustrato come aggiungere la struttura per tipi specifici di parentesi graffe.|
|[Procedura dettagliata: Visualizzazione di parentesi graffe corrispondentiWalkthrough: Display matching braces](../extensibility/walkthrough-displaying-matching-braces.md)|Viene illustrato come evidenziare le parentesi graffe corrispondenti.|
|[Procedura dettagliata: Visualizzare le descrizioni comandi di informazioni rapideWalkthrough: Display QuickInfo tooltips](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Viene illustrato come visualizzare popup di informazioni rapide che descrivono elementi di codice quali proprietà, metodi ed eventi.|
|[Procedura dettagliata: Visualizzare la Guida della firmaWalkthrough: Display signature help](../extensibility/walkthrough-displaying-signature-help.md)|Viene illustrato come visualizzare popup che forniscono informazioni sul numero e i tipi di parametri in una firma.|
|[Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)|Viene illustrato come implementare il completamento delle istruzioni.|
|[Procedura dettagliata: Implementare frammenti di codiceWalkthrough: Implement code snippets](../extensibility/walkthrough-implementing-code-snippets.md)|Viene illustrato come implementare l'espansione del frammento di codice.|
|[Procedura dettagliata: Visualizzare i suggerimenti per le lampadine](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Mostra come visualizzare le lampadine per i suggerimenti sul codice.|
|[Procedura dettagliata: Usare un comando della shell con un'estensione dell'editorWalkthrough: Use a shell command with an editor extension](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Viene illustrato come associare un comando di menu in un VSPackage a un componente MEF.|
|[Procedura dettagliata: Usare un tasto di scelta rapida con un'estensione dell'editorWalkthrough: Use a shortcut key with an editor extension](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Viene illustrato come associare un collegamento di menu in un VSPackage a un componente MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Fornisce informazioni su Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Fornisce informazioni su Windows Presentation Foundation (WPF).|

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
