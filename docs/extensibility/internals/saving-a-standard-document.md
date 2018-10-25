---
title: Salvataggio di un documento Standard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 251a9a7632a9d9615302cd3c5c1bf2a406529caf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875606"
---
# <a name="saving-a-standard-document"></a>Salvataggio di un documento standard
L'ambiente gestisce il salvataggio, Salva con nome e salvare tutti i comandi. Quando un utente seleziona **salvare**, **Salva con nome**, o **Salva tutto** dal **File** dal menu o chiude la soluzione, causando un  **Salva tutto**, verifica quanto segue.  
  
 ![Editor standard](../../extensibility/internals/media/public.gif "pubblico")  
Salvare, Salva con nome e la gestione di un editor standard del comando Salva tutto  
  
 Questa procedura è descritta nei passaggi seguenti:  
  
1. Quando la **salvare** e **Salva con nome** comandi sono selezionati, l'ambiente Usa il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> del servizio per determinare la finestra del documento attivo e in questo modo gli elementi che devono essere salvate. Dopo che è noto che la finestra del documento attivo, l'ambiente Cerca il puntatore di gerarchia e l'identificatore dell'elemento (ID elemento) per il documento nella tabella documenti in esecuzione. Per altre informazioni, vedere [tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md).  
  
    Quando la **Salva tutto** comando è selezionato, l'ambiente utilizza le informazioni nella tabella documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.  
  
2. Quando la soluzione riceve un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiamata, scorre il set di elementi selezionati (vale a dire le selezioni multiple esposte dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio).  
  
3. Su ogni elemento nella selezione, la soluzione Usa il puntatore di gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodo per determinare se il **salvare** comando di menu deve essere abilitato. Se uno o più elementi vengono modificati, il **salvare** command è abilitato. Se la gerarchia Usa un editor standard, i delegati di gerarchia per l'esecuzione di query modificato lo stato per l'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> (metodo).  
  
4. Su ogni elemento selezionato è stato modificato, la soluzione Usa il puntatore di gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metodo sulle gerarchie appropriate.  
  
    È comune per la gerarchia usare un editor standard per modificare il documento. In questo caso, i dati del documento relativo oggetto tale editor deve supportare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia. Al momento della ricezione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> chiamata al metodo, il progetto deve informare l'editor che il documento viene salvato, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metodo sull'oggetto dati del documento. L'editor può consentire l'ambiente per gestire il **Salva con nome** della finestra di dialogo chiamando `Query Service` per il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfaccia. Restituisce un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia. L'editor deve quindi chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> , passando un puntatore per l'editor <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementazione tramite il `pPersistFile` parametro. L'ambiente, quindi esegue l'operazione di salvataggio e fornisce il **Salva con nome** finestra di dialogo per l'editor. L'ambiente chiama quindi tornare all'editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5. Se l'utente tenta di salvare un documento senza titolo (vale a dire, un documento non sono stato salvato in precedenza), quindi un comando Salva con nome viene effettivamente eseguito.  
  
6. Per il comando Salva con nome, l'ambiente consente di visualizzare la finestra di dialogo Salva con nome, la richiesta all'utente un nome di file.  
  
    Se è stato modificato il nome del file, quindi la gerarchia è responsabile per l'aggiornamento della cornice di documento, le informazioni nella cache chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
   Se il **Salva con nome** comando Sposta la posizione del documento e la gerarchia è sensibile al percorso del documento, quindi la gerarchia è responsabile per la consegna il proprietario della finestra del documento aperto in un'altra gerarchia. Ad esempio, ciò si verifica se il progetto rileva se il file è un file all'interno o esterno (File esterni) in relazione al progetto. Utilizzare la procedura seguente per modificare la proprietà di un file al progetto file esterni.  
  
## <a name="changing-file-ownership"></a>Modifica delle proprietà del File  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Per modificare la proprietà del file al progetto file esterni  
  
1.  Eseguire una query del servizio per il <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfaccia.  
  
     Un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> viene restituito.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) metodo per trasferire i documenti nella nuova gerarchia. La gerarchia esegue il comando Salva con nome chiama questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)