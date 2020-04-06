---
title: 'Procedura: Aprire gli editor standard Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710793"
---
# <a name="how-to-open-standard-editors"></a>Procedura: aprire gli editor standardHow to: Open standard editors
Quando si apre un editor standard, si consente all'IDE di determinare un editor standard per un tipo di file designato, anziché specificare un editor specifico del progetto per il file.

 Completare la procedura <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> seguente per implementare il metodo. Verrà aperto un file di progetto in un editor standard.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Per implementare il metodo OpenItem con un editor standardTo implement the OpenItem method with a standard editor

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> `RDT_EditLock`( ) per determinare se il file oggetto dati del documento è già aperto.

2. Se il file è già aperto, riaffiorare il file chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodo , specificando un valore di `IDO_ActivateIfOpen` per il `grfIDO` parametro.

     Se il file è aperto e il documento è di proprietà di un progetto diverso rispetto al progetto chiamante, il progetto riceve un avviso che l'editor viene aperto da un altro progetto. La finestra del file viene quindi visualizzata.

3. Se il documento non è aperto o non <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> nella`OSE_ChooseBestStdEditor`tabella documenti in esecuzione, chiamare il metodo ( ) per aprire un editor standard per il file.

     Quando si chiama il metodo , l'IDE esegue le attività seguenti:

    1. L'IDE analizza la sottochiave Editors /guidEditorType/Extensions nel Registro di sistema per determinare quale editor può aprire il file e ha la priorità più alta per eseguire questa operazione.

    2. Dopo che l'IDE ha determinato quale editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>può aprire il file, l'IDE chiama . L'implementazione dell'editor di questo metodo restituisce le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> informazioni necessarie per l'IDE chiamare e sito il documento appena aperto.

    3. Infine, l'IDE carica il documento utilizzando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>consueta interfaccia di persistenza, ad esempio .

    4. Se l'IDE ha determinato in precedenza che la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> gerarchia o l'elemento della <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> gerarchia è disponibile, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> l'IDE chiama il metodo sul progetto per ottenere un puntatore di contesto a livello di progetto da passare nuovamente con la chiamata al metodo.

4. Restituire <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> un puntatore all'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> quando l'IDE chiama il progetto se si desidera consentire all'editor ottenere contesto dal progetto.

     L'esecuzione di questo passaggio consente al progetto di offrire servizi aggiuntivi all'editor.

     Se la visualizzazione documento o l'oggetto visualizzazione documento è stata individuata correttamente in una cornice di finestra, l'oggetto viene inizializzato con i relativi dati chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Aprire e salvare elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: aprire editor specifici del progettoHow to: Open project-specific editors](../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: aprire gli editor per i documenti apertiHow to: Open editors for open documents](../extensibility/how-to-open-editors-for-open-documents.md)
- [Visualizzare i file utilizzando il comando Apri file](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
