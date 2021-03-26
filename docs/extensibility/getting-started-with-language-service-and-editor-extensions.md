---
title: Introduzione alle estensioni dell'editor e dei servizi di linguaggio
description: Informazioni su come aggiungere funzionalità del servizio di linguaggio a qualsiasi tipo di contenuto e personalizzare l'aspetto e il comportamento dell'editor di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1afec04882d5d52bffac509dd1d1202ccf9ea449
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057611"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Introduzione alle estensioni dell'editor e dei servizi di linguaggio

È possibile utilizzare le estensioni dell'editor per aggiungere funzionalità del servizio di linguaggio come la struttura, la corrispondenza tra parentesi graffe, IntelliSense e le lampadine al proprio linguaggio di programmazione o a qualsiasi tipo di contenuto. È anche possibile personalizzare l'aspetto e il comportamento dell'editor di Visual Studio, ad esempio la colorazione del testo, i margini, le aree di disegno e altri elementi visivi. È anche possibile definire un tipo di contenuto personalizzato e specificare l'aspetto e il comportamento delle visualizzazioni di testo in cui viene visualizzato il contenuto.

 Per iniziare a scrivere le estensioni dell'editor, usare i modelli di progetto dell'editor installati come parte di Visual Studio SDK. Visual Studio SDK è un set scaricabile di strumenti che semplificano lo sviluppo di estensioni di Visual Studio, usando VSPackage o usando il Managed Extensibility Framework (MEF).

> [!NOTE]
> Per ulteriori informazioni su Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Prima di scrivere estensioni di editor, è consigliabile acquisire familiarità con i concetti e le tecnologie seguenti.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Le estensioni di Windows Presentation Foundation (WPF) ed editor

 L'interfaccia utente dell'editor di Visual Studio viene implementata usando il Windows Presentation Foundation (WPF). WPF offre un'esperienza visiva avanzata e un modello di programmazione coerente che separa gli aspetti visivi del codice dalla logica di business. È possibile utilizzare molti elementi e funzionalità WPF quando si creano le estensioni dell'editor. Per ulteriori informazioni, vedere [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Le estensioni di Managed Extensibility Framework (MEF) ed editor

 L'editor di Visual Studio usa il Managed Extensibility Framework (MEF) per gestire i componenti e le estensioni. MEF consente inoltre agli sviluppatori di creare in modo più semplice estensioni per un'applicazione host come Visual Studio. In questo Framework si definisce un'estensione in base a un contratto MEF ed è possibile esportarla come parte del componente MEF. L'applicazione host gestisce le parti del componente cercandoli, eseguendone la registrazione e assicurandosi che vengano applicati al contesto corretto.

> [!NOTE]
> Per ulteriori informazioni su MEF nell'editor, vedere [Managed Extensibility Framework nell'editor](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Estensioni e punti di estensione dell'editor di Visual Studio

 I punti di estensione dell'editor sono parti del componente MEF che è possibile personalizzare ed estendere. In alcuni casi il punto di estensione viene esteso implementando un'interfaccia ed esportandola insieme ai metadati corretti. In altri casi è sufficiente dichiarare un'estensione ed esportarla come un tipo particolare.

 Di seguito sono riportati alcuni dei tipi di base delle estensioni dell'Editor:

- Margini e barre di scorrimento

- Tag

- Aree

- Opzioni

- IntelliSense

  Per ulteriori informazioni sui punti di estensione dell'editor, vedere il [servizio di linguaggio e i punti di estensione dell'editor](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Distribuzione delle estensioni dell'editor

 In Visual Studio è possibile distribuire le estensioni dell'editor aggiungendo un file di metadati denominato *source. Extension. vsixmanifest* alla soluzione, compilando la soluzione e quindi aggiungendo una copia dei file binari e del manifesto in una cartella nota a Visual Studio. Il file manifesto definisce i fatti di base relativi all'estensione, ad esempio nome, autore, versione e tipo di contenuto. Per ulteriori informazioni sul file manifesto VSIX e su come distribuire le estensioni, vedere la pagina relativa alle [estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Quando si installa un'estensione in un computer, includere i file binari e il manifesto in una sottocartella della cartella nota in Visual Studio.

> [!WARNING]
> Non è necessario preoccuparsi dei dettagli di manifesti e percorsi di distribuzione se si usa uno dei modelli di estendibilità dell'editor inclusi in Visual Studio. I modelli contengono tutti gli elementi necessari per registrare e distribuire un'estensione.

## <a name="run-extensions-in-the-experimental-instance"></a>Eseguire le estensioni nell'istanza sperimentale

 È possibile isolare la versione di lavoro di Visual Studio durante lo sviluppo di un'estensione mediante la relativa distribuzione nella seguente cartella sperimentale (in Windows Vista e Windows 7):

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {ExtensionID}*

 dove *% LocalAppData%* è il nome dell'utente che ha eseguito l'accesso, *Company* è il nome della società che possiede l'estensione e *ExtensionID* è l'ID dell'estensione.

 Quando si distribuisce un'estensione nel percorso sperimentale, questa viene eseguita in modalità di debug. Viene avviata una seconda istanza di Visual Studio, denominata **Microsoft Visual Studio istanza sperimentale**.

## <a name="manage-extensions"></a>Gestire le estensioni

 Le estensioni di Visual Studio sono elencate in **estensioni e aggiornamenti** (dal menu **strumenti** ). Se si sta testando un'estensione nell'istanza sperimentale, questa viene elencata in **estensioni e aggiornamenti** nell'istanza sperimentale, ma non è elencata nell'istanza di sviluppo.

 Per altre informazioni, vedere [trovare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Usare i modelli per creare le estensioni dell'editor

 È possibile utilizzare modelli di editor per creare estensioni MEF che consentono di personalizzare i classificatori, le aree di strumenti e i margini. Sono disponibili modelli per progetti C# e Visual Basic. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 È anche possibile usare il modello di progetto VSIX per creare estensioni. Questo modello fornisce solo gli elementi necessari per distribuire qualsiasi tipo di estensione e include il file *source. Extension. vsixmanifest* , i riferimenti agli assembly necessari e un file di progetto che include le attività di compilazione che consentono di distribuire l'estensione. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

 È anche possibile creare componenti MEF dell'editor da un'estensione del pacchetto di Visual Studio. Per informazioni dettagliate, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: uso di un comando della shell con un'estensione dell'editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Procedura dettagliata: utilizzo di un tasto di scelta rapida con un'estensione dell'editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Vedi anche

- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
