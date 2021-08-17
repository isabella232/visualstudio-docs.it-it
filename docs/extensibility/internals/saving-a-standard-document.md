---
title: Salvataggio di un documento standard | Microsoft Docs
description: Informazioni sul processo che si verifica per un documento standard per un tipo di progetto aggiunto all'IDE Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 71e4aaa99a17e8643af104a30e12caf3300e0570a00cc1715d80016333aff64f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375657"
---
# <a name="saving-a-standard-document"></a>Salvataggio di un documento standard
L'ambiente gestisce i comandi Salva, Salva con nome e Salva tutto. Quando un utente seleziona **Salva** **,** Salva con nome o Salva tutto dal menu **File** o chiude la soluzione, determinando un'operazione Salva  **tutto**, si verifica il processo seguente.

 ![Editor standard](../../extensibility/internals/media/public.gif "Pubblico") Gestione dei comandi Salva, Salva con nome e Salva tutto per un editor standard

 Questo processo è descritto in dettaglio nei passaggi seguenti:

1. Quando i **comandi Salva** e Salva **con nome** sono selezionati, l'ambiente usa il servizio per determinare la finestra del documento attiva e quindi gli elementi <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> da salvare. Una volta nota la finestra del documento attivo, l'ambiente trova il puntatore della gerarchia e l'identificatore dell'elemento (itemID) per il documento nella tabella del documento in esecuzione. Per altre informazioni, vedere [Running Document Table](../../extensibility/internals/running-document-table.md).

    Quando si **seleziona il comando Salva** tutto, l'ambiente usa le informazioni nella tabella dei documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.

2. Quando la soluzione riceve una chiamata, scorre il set di elementi selezionati, ovvero le selezioni multiple esposte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio.

3. Per ogni elemento nella selezione, la soluzione usa il puntatore della gerarchia per chiamare il metodo per determinare se il comando di menu Salva <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> deve essere abilitato.  Se uno o più elementi sono dirty, il **comando Salva** è abilitato. Se la gerarchia usa un editor standard, la gerarchia delega l'esecuzione di query per lo stato dirty all'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metodo .

4. In ogni elemento selezionato modificato, la soluzione usa il puntatore della gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metodo sulle gerarchie appropriate.

    È normale che la gerarchia usi un editor standard per modificare il documento. In questo caso, l'oggetto dati del documento per tale editor deve supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> l'interfaccia . Quando si riceve la chiamata al metodo , il progetto deve informare l'editor che il documento viene salvato chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metodo sull'oggetto dati del documento. L'editor può consentire all'ambiente di gestire la finestra di **dialogo Salva** con nome chiamando `Query Service` per <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> l'interfaccia . Viene restituito un puntatore <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> all'interfaccia . L'editor deve quindi chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> il metodo , passando un puntatore all'implementazione dell'editor tramite il parametro <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> `pPersistFile` . L'ambiente esegue quindi l'operazione di salvataggio e fornisce la **finestra di dialogo Salva** con nome per l'editor. L'ambiente richiama quindi all'editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .

5. Se l'utente sta tentando di salvare un documento senza titolo, ovvero un documento non salvato in precedenza, viene effettivamente eseguito un comando Salva con nome.

6. Per il comando Salva con nome, nell'ambiente viene visualizzata la finestra di dialogo Salva con nome che richiede all'utente un nome file.

    Se il nome del file è stato modificato, la gerarchia è responsabile dell'aggiornamento delle informazioni memorizzate nella cache del frame del documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> chiamando (VSFPROPID_MkDocument).

   Se il **comando Salva** con nome sposta il percorso del documento e la gerarchia è sensibile al percorso del documento, la gerarchia è responsabile della consegna della proprietà della finestra del documento aperta a un'altra gerarchia. Ad esempio, ciò si verifica se il progetto rileva se il file è interno o esterno (File esterno) in relazione al progetto. Utilizzare la procedura seguente per modificare la proprietà di un file nel progetto File esterni.

## <a name="changing-file-ownership"></a>Modifica della proprietà dei file

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Per modificare la proprietà del file nel progetto File esterni

1. Servizio query per <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> l'interfaccia.

     Viene restituito <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> un puntatore a .

2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> metodo ( , ) per trasferire il documento nella nuova `pszMkDocumentNew` `punkWindowFrame` gerarchia. La gerarchia che esegue il comando Salva con nome chiama questo metodo.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
