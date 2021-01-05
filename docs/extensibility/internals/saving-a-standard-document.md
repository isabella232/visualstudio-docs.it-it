---
title: Salvataggio di un documento standard | Microsoft Docs
description: Informazioni sul processo che si verifica per un documento standard per un tipo di progetto aggiunto all'IDE di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81c79ece83bc8aaaf7ca4dd28642de5973ad94c1
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875666"
---
# <a name="saving-a-standard-document"></a>Salvataggio di un documento standard
L'ambiente gestisce i comandi Salva, Salva con nome e Salva tutti. Quando un utente seleziona **Salva**, **Salva con nome** o **Salva tutto** dal menu **file** o chiude la soluzione, generando un' **eccezione Salva tutto**, si verifica il processo seguente.

 ![Editor standard](../../extensibility/internals/media/public.gif "Pubblico") Salva, Salva con nome e Salva tutte le operazioni di gestione dei comandi per un editor standard

 Questo processo è descritto in dettaglio nei passaggi seguenti:

1. Quando si selezionano i comandi **Salva** e **Salva con nome** , l'ambiente USA il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio per determinare la finestra del documento attiva e quindi gli elementi da salvare. Quando la finestra del documento attivo è nota, l'ambiente trova il puntatore della gerarchia e l'identificatore dell'elemento (itemID) per il documento nella tabella documenti in esecuzione. Per ulteriori informazioni, vedere [esecuzione della tabella documenti](../../extensibility/internals/running-document-table.md).

    Quando si seleziona il comando **Salva tutto** , l'ambiente utilizza le informazioni nella tabella documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.

2. Quando la soluzione riceve una <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiamata, scorre il set di elementi selezionati, ovvero le selezioni multiple esposte dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio.

3. Per ogni elemento della selezione, la soluzione USA il puntatore della gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodo per determinare se il comando di menu **Salva** deve essere abilitato. Se uno o più elementi sono Dirty, il comando **Salva** è abilitato. Se la gerarchia usa un editor standard, la gerarchia delega la query per lo stato dirty all'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metodo.

4. Per ogni elemento selezionato Dirty, la soluzione USA il puntatore della gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Metodo sulle gerarchie appropriate.

    È normale che la gerarchia usi un editor standard per modificare il documento. In questo caso, l'oggetto dati del documento per l'editor deve supportare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia. Al momento della ricezione della <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> chiamata al metodo, il progetto deve informare l'editor che il documento viene salvato chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metodo sull'oggetto dati del documento. L'editor può consentire all'ambiente di gestire la finestra di dialogo **Salva con nome** , chiamando `Query Service` per l' <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfaccia. Viene restituito un puntatore all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia. L'editor deve quindi chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> metodo, passando un puntatore all'implementazione dell'editor <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> tramite il `pPersistFile` parametro. L'ambiente esegue quindi l'operazione di salvataggio e fornisce la finestra di dialogo **Salva con nome** per l'editor. L'ambiente richiama quindi l'editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .

5. Se l'utente tenta di salvare un documento senza titolo, ovvero un documento precedentemente non salvato, viene effettivamente eseguito un comando Salva con nome.

6. Per il comando Salva con nome, l'ambiente Visualizza la finestra di dialogo Salva con nome, in cui viene richiesto all'utente un nome file.

    Se il nome del file è stato modificato, la gerarchia è responsabile dell'aggiornamento delle informazioni memorizzate nella cache del frame del documento chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).

   Se il comando **Salva con nome** sposta il percorso del documento e la gerarchia è sensibile al percorso del documento, la gerarchia è responsabile della consegna della proprietà della finestra Apri documento a un'altra gerarchia. Questa situazione si verifica, ad esempio, se il progetto rileva se il file è un file interno o esterno (file vario) in relazione al progetto. Utilizzare la procedura seguente per modificare la proprietà di un file nel progetto di file esterni.

## <a name="changing-file-ownership"></a>Modifica della proprietà del file

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Per modificare la proprietà del file nel progetto di file esterni

1. Servizio query per l' <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfaccia.

     Viene restituito un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> .

2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> `pszMkDocumentNew` Metodo (, `punkWindowFrame` ) per trasferire il documento alla nuova gerarchia. La gerarchia che esegue il comando Salva con nome chiama questo metodo.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
