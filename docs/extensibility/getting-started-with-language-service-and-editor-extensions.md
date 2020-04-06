---
title: Guida introduttiva al Servizio di linguaggio e alle estensioni dell'editor Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711303"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Introduzione al servizio di linguaggio e alle estensioni dell'editor
È possibile usare le estensioni dell'editor per aggiungere funzionalità del servizio di linguaggio, ad esempio struttura, corrispondenza parentesi graffe, IntelliSense e lampadine al proprio linguaggio di programmazione o a qualsiasi tipo di contenuto. È inoltre possibile personalizzare l'aspetto e il comportamento dell'editor di Visual Studio, ad esempio la colorazione del testo, i margini, le aree di controllo e altri elementi visivi. È inoltre possibile definire un tipo di contenuto personalizzato e specificare l'aspetto e il comportamento delle visualizzazioni di testo in cui viene visualizzato il contenuto.

 Per iniziare a scrivere le estensioni dell'editor, usare i modelli di progetto dell'editor installati come parte di Visual Studio SDK. Visual Studio SDK è un set scaricabile di strumenti che semplificano lo sviluppo delle estensioni di Visual Studio, tramite VSPackage o Managed Extensibility Framework (MEF).

> [!NOTE]
> Per ulteriori informazioni su Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Si consiglia di apprendere i concetti e le tecnologie seguenti prima di scrivere le estensioni dell'editor personalizzate.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Le estensioni di Windows Presentation Foundation (WPF) e dell'editor
 L'interfaccia utente dell'editor di Visual Studio viene implementata tramite Windows Presentation Foundation (WPF). WPFWPF offre un'esperienza visiva avanzata e un modello di programmazione coerente che separa gli aspetti visivi del codice dalla logica di business. È possibile usare molti elementi e funzionalità WPFWPF quando si creano estensioni dell'editor. Per ulteriori informazioni, vedere [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) e le estensioni dell'editor
 L'editor di Visual Studio utilizza Managed Extensibility Framework (MEF) per gestire i relativi componenti ed estensioni. MEF consente inoltre agli sviluppatori di creare più facilmente estensioni per un'applicazione host come Visual Studio.The MEF also lets developers more easily create extensions for a host application like Visual Studio. In questo framework, si definisce un'estensione in base a un contratto MEF ed esportarla come parte componente MEF. L'applicazione host gestisce le parti componenti individuandole, registrandole e verificando che vengano applicate al contesto corretto.

> [!NOTE]
> Per ulteriori informazioni su MEF nell'editor, vedere [Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Punti di estensione ed estensioni dell'editor di Visual StudioVisual Studio editor extension points and extensions
 I punti di estensione dell'editor sono parti del componente MEF che è possibile personalizzare ed estendere. In alcuni casi si estende il punto di estensione implementando un'interfaccia ed esportandolo insieme ai metadati corretti. In altri casi è sufficiente dichiarare un'estensione ed esportarla come un tipo particolare.

 Di seguito sono riportati alcuni dei tipi di base delle estensioni dell'editor:

- Margini e barre di scorrimento

- Tag

- Ornamenti

- Opzioni

- IntelliSense

  Per ulteriori informazioni sui punti di estensione dell'editor, vedere Punti di estensione del servizio di linguaggio [e dell'editor](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Distribuzione delle estensioni del editorDeploying editor extensions
 In Visual Studio è possibile distribuire le estensioni dell'editor aggiungendo un file di metadati denominato *source.extension.vsixmanifest* alla soluzione, compilando la soluzione e quindi aggiungendo una copia dei file binari e il manifesto in una cartella nota a Visual Studio. Il file manifesto definisce i fatti di base sull'estensione (ad esempio, nome, autore, versione e tipo di contenuto). Per ulteriori informazioni sul file manifesto VSIX e su come distribuire le estensioni, vedere [Spedire le estensioni](../extensibility/shipping-visual-studio-extensions.md)di Visual Studio .

 Quando si installa un'estensione in un computer, includere i file binari e il manifesto in una sottocartella della cartella nota a Visual Studio.

> [!WARNING]
> Non è necessario preoccuparsi dei dettagli dei manifesti e dei percorsi di distribuzione se si utilizza uno dei modelli di estensibilità dell'editor inclusi in Visual Studio. I modelli contengono tutto ciò che è necessario per registrare e distribuire un'estensione.

## <a name="run-extensions-in-the-experimental-instance"></a>Eseguire estensioni nell'istanza sperimentaleRun extensions in the experimental instance
 È possibile isolare la versione di lavoro di Visual Studio durante lo sviluppo di un'estensione distribuendola nella seguente cartella sperimentale (in Windows Vista e Windows 7):

 *"%LOCALAPPDATA%" (VisualStudio) 10.0 Exp (Estensioni)\\(Società)\\*

 dove *%LOCALAPPDATA%* è il nome dell'utente connesso, *Società* è il nome della società proprietaria dell'estensione e *ExtensionID* è l'ID dell'estensione.

 Quando si distribuisce un'estensione nel percorso sperimentale, viene eseguita in modalità di debug. Viene avviata una seconda istanza di Visual Studio denominata **Microsoft Visual Studio - Istanza sperimentale**.

## <a name="manage-extensions"></a>Gestire le estensioni
 Le estensioni di Visual Studio sono elencate in **Estensioni e aggiornamenti** (nel menu **Strumenti).** Se si sta testando un'estensione nell'istanza sperimentale, viene elencata in **Estensioni e aggiornamenti** nell'istanza sperimentale, ma non è elencata nell'istanza di sviluppo.

 Per ulteriori informazioni, vedere [Trovare e utilizzare le estensioni](../ide/finding-and-using-visual-studio-extensions.md)di Visual Studio.

## <a name="use-templates-to-create-editor-extensions"></a>Usare i modelli per creare estensioni dell'editorUse templates to create editor extensions
 È possibile utilizzare i modelli di editor per creare estensioni MEF che personalizzano classificatori, aree di controllo e margini. Sono disponibili modelli sia per i progetti di C, sia per i progetti Visual Basic. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

 È anche possibile usare il modello di progetto VSIX per creare estensioni. Questo modello fornisce solo gli elementi necessari per distribuire qualsiasi tipo di estensione e includere il file *source.extension.vsixmanifest,* i riferimenti all'assembly necessari e un file di progetto che include le attività di compilazione che consentono di distribuire l'estensione. Per ulteriori informazioni, vedere modello di [progetto VSIX](../extensibility/vsix-project-template.md).

 È anche possibile creare componenti MEF dell'editor da un'estensione del pacchetto di Visual Studio.You can also create editor MEF components from a Visual Studio Package extension. Per informazioni dettagliate, vedere le procedure dettagliate seguenti:See the following walkthroughs for details:

- [Procedura dettagliata: utilizzo di un comando della shell con un'estensione dell'editorWalkthrough: Using a shell command with an editor extension](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Procedura dettagliata: utilizzo di un tasto di scelta rapida con un'estensione dell'editorWalkthrough: Using a shortcut key with an editor extension](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
