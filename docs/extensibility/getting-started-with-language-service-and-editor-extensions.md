---
title: Introduzione alle estensioni del servizio di linguaggio e dell'editor
description: Informazioni su come aggiungere funzionalità del servizio di linguaggio a qualsiasi tipo di contenuto e personalizzare l'aspetto e il comportamento dell Visual Studio editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b9518179b0096dcb7527ea5e9eba4e72cbc70727c7d6f73af4b59f6cb22d08cc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359975"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Introduzione alle estensioni del servizio di linguaggio e dell'editor

È possibile usare le estensioni dell'editor per aggiungere funzionalità del servizio di linguaggio come la struttura, la corrispondenza delle parentesi graffe, IntelliSense e le lampadine al linguaggio di programmazione o a qualsiasi tipo di contenuto. È anche possibile personalizzare l'aspetto e il comportamento dell'editor Visual Studio, ad esempio la colorazione del testo, i margini, le aree di controllo e altri elementi visivi. È anche possibile definire un tipo di contenuto personalizzato e specificare l'aspetto e il comportamento delle visualizzazioni testo in cui viene visualizzato il contenuto.

 Per iniziare a scrivere le estensioni dell'editor, usare i modelli di progetto dell'editor installati come parte di Visual Studio SDK. Visual Studio SDK è un set scaricabile di strumenti che semplificano lo sviluppo di estensioni Visual Studio, tramite VSPackage o tramite Managed Extensibility Framework (MEF).

> [!NOTE]
> Per altre informazioni sull'SDK Visual Studio, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

 È consigliabile acquisire informazioni sui concetti e sulle tecnologie seguenti prima di scrivere estensioni dell'editor personalizzate.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Estensioni Windows Presentation Foundation (WPF) e dell'editor

 L Visual Studio'interfaccia utente dell'editor di applicazioni viene implementata usando Windows Presentation Foundation (WPF). WPF offre un'esperienza visiva complessa e un modello di programmazione coerente che separa gli aspetti visivi del codice dalla logica di business. Quando si creano estensioni dell'editor, è possibile usare molti elementi e funzionalità WPF. Per altre informazioni, vedere [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Estensioni Managed Extensibility Framework (MEF) e dell'editor

 L Visual Studio editor usa Managed Extensibility Framework (MEF) per gestire i componenti e le estensioni. MEF consente inoltre agli sviluppatori di creare più facilmente estensioni per un'applicazione host come Visual Studio. In questo framework si definisce un'estensione in base a un contratto MEF e la si esporta come parte del componente MEF. L'applicazione host gestisce le parti del componente individuandole, registrandole e assicurando che siano applicate al contesto corretto.

> [!NOTE]
> Per altre informazioni sul file MEF nell'editor, vedere [Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio estensioni e punti di estensione dell'editor di applicazioni

 I punti di estensione dell'editor sono parti del componente MEF che è possibile personalizzare ed estendere. In alcuni casi si estende il punto di estensione implementando un'interfaccia ed esportandola insieme ai metadati corretti. In altri casi è sufficiente dichiarare un'estensione ed esportarla come tipo specifico.

 Di seguito sono riportati alcuni dei tipi di base delle estensioni dell'editor:

- Margini e barre di scorrimento

- Tag

- Ornamenti

- Opzioni

- IntelliSense

  Per altre informazioni sui punti di estensione dell'editor, vedere Punti [di estensione del servizio di linguaggio e dell'editor.](../extensibility/language-service-and-editor-extension-points.md)

## <a name="deploying-editor-extensions"></a>Distribuzione delle estensioni dell'editor

 In Visual Studio le estensioni dell'editor vengono distribuite aggiungendo un file di metadati denominato *source.extension.vsixmanifest* alla soluzione, compilando la soluzione e quindi aggiungendo una copia dei file binari e del manifesto in una cartella nota a Visual Studio. Il file manifesto definisce i fatti di base sull'estensione ,ad esempio nome, autore, versione e tipo di contenuto. Per altre informazioni sul file manifesto VSIX e su come distribuire le estensioni, vedere [Ship Visual Studio extensions](../extensibility/shipping-visual-studio-extensions.md).

 Quando si installa un'estensione in un computer, includere i file binari e il manifesto in una sottocartella della cartella nota per Visual Studio.

> [!WARNING]
> Non è necessario preoccuparsi dei dettagli dei manifesti e dei percorsi di distribuzione se si usa uno dei modelli di estendibilità dell'editor inclusi in Visual Studio. I modelli contengono tutti gli elementi necessari per registrare e distribuire un'estensione.

## <a name="run-extensions-in-the-experimental-instance"></a>Eseguire le estensioni nell'istanza sperimentale

 È possibile isolare la versione funzionante di Visual Studio durante lo sviluppo di un'estensione distribuerla nella cartella sperimentale seguente (in Windows Vista e Windows 7):

 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions \\ {Company} \\ {ExtensionID}*

 dove *%LOCALAPPDATA%* è il nome dell'utente connesso, *Company* è il nome della società proprietaria dell'estensione e *ExtensionID* è l'ID dell'estensione.

 Quando si distribuisce un'estensione nel percorso sperimentale, viene eseguita in modalità di debug. Viene avviata una seconda istanza Visual Studio e viene denominata **Microsoft Visual Studio - Istanza sperimentale**.

## <a name="manage-extensions"></a>Gestire le estensioni

 Le estensioni Visual Studio sono elencate in **Estensioni e aggiornamenti** (nel menu Strumenti).  Se si sta testando un'estensione nell'istanza sperimentale, questa viene elencata in **Estensioni** e aggiornamenti nell'istanza sperimentale, ma non è elencata nell'istanza di sviluppo.

 Per altre informazioni, vedere [Trovare e usare Visual Studio estensioni](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Usare i modelli per creare estensioni dell'editor

 È possibile usare i modelli dell'editor per creare estensioni MEF che personalizzano classificatori, aree di controllo e margini. Sono disponibili modelli per i progetti C# e Visual Basic progetto. Per altre informazioni, vedere Creare [un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

 È anche possibile usare il modello di Project VSIX per creare estensioni. Questo modello fornisce solo gli elementi necessari per distribuire qualsiasi tipo di estensione e include il file *source.extension.vsixmanifest,* i riferimenti agli assembly necessari e un file di progetto che include le attività di compilazione che consentono di distribuire l'estensione. Per altre informazioni, vedere [Modello di progetto VSIX.](../extensibility/vsix-project-template.md)

 È anche possibile creare componenti MEF dell'editor da un'Visual Studio pacchetto. Per informazioni dettagliate, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: Uso di un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Procedura dettagliata: Uso di un tasto di scelta rapida con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Vedi anche

- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
