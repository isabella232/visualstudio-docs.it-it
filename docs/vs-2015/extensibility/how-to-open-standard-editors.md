---
title: 'Procedura: Aprire gli editor Standard | Microsoft Docs'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042536"
---
# <a name="how-to-open-standard-editors"></a>Procedura: Aprire gli editor standard
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si apre un editor standard, è consentire l'IDE di determinare un editor standard per un tipo di file, anziché specificare un editor specifico del progetto per il file.  
  
 Completare la procedura seguente per implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> (metodo). Si aprirà un file di progetto in un editor standard.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Per implementare il metodo OpenItem con un editor standard  
  
1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) per determinare se il file di oggetto dati documento è già aperto.  
  
2. Se il file è già aperto, il file resurface chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodo, specificando il valore `IDO_ActivateIfOpen` per il `grfIDO` parametro.  
  
     Se il file è aperto e il documento è di proprietà da un progetto diverso rispetto al progetto chiamante, il progetto specifico riceve un avviso che l'editor viene aperto da un altro progetto. Finestra di dialogo file viene quindi esposto.  
  
3. Se il documento non è aperto o non nella tabella documenti in esecuzione, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo (`OSE_ChooseBestStdEditor`) per aprire un editor standard per il file.  
  
     Quando si chiama il metodo, l'IDE esegue le attività seguenti:  
  
    1. L'IDE analizza gli editor / {guidEditorType} / estensioni sottochiave del Registro di sistema per determinare quale editor può aprire il file e ha la priorità più alta per eseguire questa operazione.  
  
    2. Dopo che l'IDE ha determinato quale editor può aprire il file, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Implementazione dell'editor di questo metodo restituisce informazioni necessarie per l'IDE chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> e del sito del documento appena aperto.  
  
    3. Infine, l'IDE carica il documento usando l'interfaccia di persistenza consueto, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4. Se l'IDE in precedenza ha determinato che la gerarchia o l'elemento della gerarchia è disponibile, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> metodo nel progetto per ottenere un contesto a livello di progetto <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> puntatore da passare nuovamente con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> chiamata al metodo.  
  
4. Restituisce un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> puntatore all'IDE quando si chiama l'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> sul progetto se si vuole consentire la scelta rapida get editor dal progetto.  
  
     Eseguire questo passaggio consente i servizi aggiuntivi di offerta di progetto nell'editor.  
  
     Se la visualizzazione del documento o un oggetto visualizzazione del documento è stato individuato correttamente in una cornice di finestra, l'oggetto viene inizializzato con i relativi dati tramite una chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: Apri editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: Aprire gli editor per i documenti aperti](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Visualizzazione di file tramite il comando Apri file](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
