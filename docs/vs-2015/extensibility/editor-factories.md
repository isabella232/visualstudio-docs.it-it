---
title: Factory dell'editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197755"
---
# <a name="editor-factories"></a>Factory editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una factory dell'editor crea oggetti Editor e li inserisce in una cornice di finestra, nota come visualizzazione fisica. Vengono creati gli oggetti dati del documento e visualizzazione documento necessari per la creazione di editor e finestre di progettazione. Per creare l'editor principale di Visual Studio e qualsiasi editor standard, è necessaria una factory dell'editor. È anche possibile creare un editor personalizzato con una factory dell'editor.  
  
 Si crea una factory dell'editor implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia. Nell'esempio seguente viene illustrato come implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> per creare una factory dell'Editor:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Un editor viene caricato la prima volta che si apre un tipo di file gestito da tale editor. È possibile scegliere di aprire un editor specifico o l'editor predefinito. Se si seleziona l'editor predefinito, il Integrated Development Environment (IDE) determina l'editor corretto per aprirlo e quindi aprirlo. Per ulteriori informazioni, vedere [determinazione dell'editor che apre un file in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registrazione di Factory Editor  
 Prima di poter usare un editor creato, è necessario prima registrarvi le informazioni, incluse le estensioni di file che è in grado di gestire.  
  
 Se il pacchetto VSPackage è scritto in codice gestito, è possibile usare il metodo del Framework di pacchetto gestito (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> per registrare la factory dell'editor dopo il caricamento del pacchetto VSPackage. Se il pacchetto VSPackage è scritto in codice non gestito, è necessario registrare la factory dell'editor usando il <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> servizio.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrazione di una factory dell'editor tramite codice gestito  
 È necessario registrare la factory dell'editor nel metodo del pacchetto VSPackage `Initialize` . Prima chiamata `base.Initialize` , quindi chiamare <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> per ogni factory dell'editor  
  
 Nel codice gestito non è necessario annullare la registrazione di una factory dell'editor, perché il pacchetto VSPackage gestirà questa operazione. Inoltre, se la factory dell'editor implementa <xref:System.IDisposable> , viene automaticamente eliminata quando viene annullata la registrazione.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registrazione di una factory dell'editor tramite codice non gestito  
 Nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione per il pacchetto dell'editor usare il `QueryService` metodo per chiamare `SVsRegisterEditors` . Questa operazione restituisce un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodo passando l'implementazione dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia. È necessario mplementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> in una classe separata.  
  
## <a name="the-editor-factory-registration-process"></a>Processo di registrazione della factory dell'editor  
 Il processo seguente si verifica quando Visual Studio carica l'editor tramite la factory dell'Editor:  
  
1. Il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sistema del progetto chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Questo metodo restituisce la factory dell'editor. Visual Studio ritarda il caricamento del pacchetto dell'editor, tuttavia, fino a quando un sistema di progetto non necessita effettivamente dell'editor.  
  
3. Quando un sistema di progetto necessita dell'editor, Visual Studio chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , un metodo specializzato che restituisce sia la visualizzazione del documento che gli oggetti dati del documento.  
  
4. Se chiama da Visual Studio alla factory dell'editor usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Restituisci un oggetto dati del documento e un oggetto visualizzazione del documento, Visual Studio crea quindi la finestra del documento, vi inserisce l'oggetto visualizzazione del documento ed esegue una voce nella tabella documenti in esecuzione (RDT) per l'oggetto dati del documento.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabella documenti in esecuzione](../extensibility/internals/running-document-table.md)
