---
title: 'Procedura: aprire gli editor standard | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 792ac8a0859481fd97b2eaee4bd66753f0460a37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204126"
---
# <a name="how-to-open-standard-editors"></a>Procedura: Aprire gli editor standard
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si apre un editor standard, si consente all'IDE di determinare un editor standard per un tipo di file designato, anziché specificare un editor specifico del progetto per il file.  
  
 Completare la procedura seguente per implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo. Verrà aperto un file di progetto in un editor standard.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Per implementare il Metodo OpenItem con un editor standard  
  
1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> ( `RDT_EditLock` ) per determinare se il file oggetto dati del documento è già aperto.  
  
2. Se il file è già aperto, riesporre il file chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodo, specificando il valore `IDO_ActivateIfOpen` per il `grfIDO` parametro.  
  
     Se il file è aperto e il documento è di proprietà di un progetto diverso da quello del progetto chiamante, il progetto riceve un avviso che indica che l'Editor aperto è da un altro progetto. La finestra del file viene quindi rilevata.  
  
3. Se il documento non è aperto o non è presente nella tabella documenti in esecuzione, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Metodo ( `OSE_ChooseBestStdEditor` ) per aprire un editor standard per il file.  
  
     Quando si chiama il metodo, l'IDE esegue le attività seguenti:  
  
    1. L'IDE analizza la sottochiave Editors/{guidEditorType}/Extensions nel registro di sistema per determinare quale editor può aprire il file e ha la priorità più elevata per questa operazione.  
  
    2. Dopo che l'IDE ha determinato quale editor è in grado di aprire il file, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . L'implementazione dell'editor di questo metodo restituisce le informazioni necessarie per l'IDE per chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> e il sito del documento appena aperto.  
  
    3. Infine, l'IDE carica il documento usando la consueta interfaccia di persistenza, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .  
  
    4. Se l'IDE ha rilevato in precedenza che la gerarchia o l'elemento della gerarchia è disponibile, l'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> metodo sul progetto per ottenere un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> puntatore di contesto a livello di progetto da passare nuovamente con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> chiamata al metodo.  
  
4. Restituisce un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> puntatore all'IDE quando l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> sul progetto se si vuole consentire all'editor di ottenere il contesto dal progetto.  
  
     L'esecuzione di questo passaggio consente al progetto di offrire servizi aggiuntivi all'editor.  
  
     Se la visualizzazione del documento o dell'oggetto visualizzazione del documento è stata eseguita correttamente in una cornice della finestra, l'oggetto viene inizializzato con i relativi dati chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: aprire editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: aprire Editor per documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Visualizzazione di file tramite il comando Apri file](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
