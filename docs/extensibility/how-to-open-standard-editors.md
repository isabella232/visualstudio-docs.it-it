---
title: 'Procedura: Aprire editor standard | Microsoft Docs'
description: Informazioni su come implementare il metodo OpenItem con un editor standard. L'IDE determina un editor standard per un tipo di file designato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dda137697f4645af166d846af9605358c7f0c489bc3ef86692f00688f50f0221
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401726"
---
# <a name="how-to-open-standard-editors"></a>Procedura: Aprire editor standard
Quando si apre un editor standard, si consente all'IDE di determinare un editor standard per un tipo di file designato, anziché specificare un editor specifico del progetto per il file.

 Completare la procedura seguente per implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo . Verrà aperto un file di progetto in un editor standard.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Per implementare il metodo OpenItem con un editor standard

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> ( ) per `RDT_EditLock` determinare se il file dell'oggetto dati del documento è già aperto.

2. Se il file è già aperto, riasare il file chiamando il metodo , specificando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> valore per il parametro `IDO_ActivateIfOpen` `grfIDO` .

     Se il file è aperto e il documento appartiene a un progetto diverso da quello chiamante, il progetto riceve un avviso che indica che l'editor aperto appartiene a un altro progetto. Viene quindi visualizzata la finestra del file.

3. Se il documento non è aperto o non è presente nella tabella del documento in esecuzione, chiamare il metodo ( ) per aprire un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> editor standard per il `OSE_ChooseBestStdEditor` file.

     Quando si chiama il metodo , l'IDE esegue le attività seguenti:

    1. L'IDE analizza la sottochiave Editors/{guidEditorType}/Extensions nel Registro di sistema per determinare quale editor può aprire il file e ha la priorità più alta per questa operazione.

    2. Dopo che l'IDE ha determinato quale editor può aprire il file, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . L'implementazione dell'editor di questo metodo restituisce le informazioni necessarie per l'IDE per chiamare e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> sito del documento appena aperto.

    3. Infine, l'IDE carica il documento usando la consueta interfaccia di persistenza, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .

    4. Se in precedenza l'IDE ha determinato che la gerarchia o l'elemento della gerarchia è disponibile, l'IDE chiama il metodo nel progetto per ottenere un puntatore di contesto a livello di progetto da passare nuovamente con la chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> al metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> .

4. Restituire un puntatore all'IDE quando l'IDE chiama il progetto se si vuole consentire all'editor di ottenere <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> il contesto dal progetto.

     L'esecuzione di questo passaggio consente al progetto di offrire servizi aggiuntivi all'editor.

     Se il sito dell'oggetto visualizzazione documento o visualizzazione documento è stato eseguito correttamente in una cornice di finestra, l'oggetto viene inizializzato con i relativi dati chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Aprire e salvare elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: Aprire editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: Aprire editor per documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)
- [Visualizzare i file usando il comando Apri file](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
