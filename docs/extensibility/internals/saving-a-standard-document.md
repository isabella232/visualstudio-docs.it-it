---
title: Salvataggio di un documento standard | Microsoft Docs
description: Informazioni sul processo che si verifica per un documento standard per un tipo di progetto aggiunto all Visual Studio IDE.
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
ms.openlocfilehash: 00dcb3d9d5f93c8c412302ad67dfa8a5bd379e12
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049532"
---
# <a name="saving-a-standard-document"></a>Salvataggio di un documento standard
L'ambiente gestisce i comandi Salva, Salva con nome e Salva tutto. Quando un utente seleziona **Salva** **,** Salva con nome o Salva tutto dal menu **File** o chiude la soluzione, con conseguente salvataggio  **di** tutti , si verifica il processo seguente.

 ![Editor standard](../../extensibility/internals/media/public.gif "Pubblico") Gestione dei comandi Salva, Salva con nome e Salva tutto per un editor standard

 Questo processo è dettagliato nei passaggi seguenti:

1. Quando i **comandi Salva** **e Salva** con nome sono selezionati, l'ambiente usa il servizio per determinare la finestra del documento attivo e quindi gli elementi <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> da salvare. Una volta nota la finestra del documento attivo, l'ambiente trova il puntatore della gerarchia e l'identificatore di elemento (itemID) per il documento nella tabella del documento in esecuzione. Per altre informazioni, vedere [Running Document Table](../../extensibility/internals/running-document-table.md).

    Quando si **seleziona il comando Salva** tutto, l'ambiente usa le informazioni nella tabella dei documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.

2. Quando la soluzione riceve una chiamata, scorre il set di elementi selezionati, ovvero le selezioni multiple esposte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio.

3. In ogni elemento nella selezione, la soluzione usa il puntatore della gerarchia per chiamare il metodo per determinare se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> **comando** di menu Salva deve essere abilitato. Se uno o più elementi sono dirty, il **comando Salva** è abilitato. Se la gerarchia usa un editor standard, la gerarchia delega la query per lo stato dirty all'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metodo .

4. In ogni elemento selezionato dirty, la soluzione usa il puntatore della gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metodo sulle gerarchie appropriate.

    È comune che la gerarchia usi un editor standard per modificare il documento. In questo caso, l'oggetto dati del documento per tale editor deve supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> l'interfaccia . Quando si riceve la chiamata al metodo , il progetto deve informare l'editor che il documento viene salvato chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metodo sull'oggetto dati del documento. L'editor può consentire all'ambiente di gestire la **finestra di** dialogo Salva con nome chiamando `Query Service` per <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> l'interfaccia . Verrà restituito un puntatore <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> all'interfaccia . L'editor deve quindi chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> il metodo , passando un puntatore all'implementazione dell'editor tramite il parametro <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> `pPersistFile` . L'ambiente esegue quindi l'operazione di salvataggio e fornisce la **finestra di** dialogo Salva con nome per l'editor. L'ambiente chiama quindi all'editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .

5. Se l'utente sta tentando di salvare un documento senza titolo, ovvero un documento non salvato in precedenza, viene effettivamente eseguito un comando Salva con nome.

6. Per il comando Salva con nome, l'ambiente visualizza la finestra di dialogo Salva con nome, in cui viene richiesto all'utente di specificare un nome di file.

    Se il nome del file è stato modificato, la gerarchia è responsabile dell'aggiornamento delle informazioni memorizzate nella cache del frame del documento chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).

   Se il **comando** Salva con nome sposta la posizione del documento e la gerarchia è sensibile al percorso del documento, la gerarchia è responsabile del trasferimento della proprietà della finestra del documento aperta a un'altra gerarchia. Ad esempio, ciò si verifica se il progetto tiene traccia se il file è un file interno o esterno (File esterno) in relazione al progetto. Usare la procedura seguente per modificare la proprietà di un file nel progetto File esterni.

## <a name="changing-file-ownership"></a>Modifica della proprietà dei file

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Per modificare la proprietà del file nel progetto File esterni

1. Servizio query per <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> l'interfaccia.

     Viene restituito <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> un puntatore a .

2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> metodo ( , ) per trasferire il documento nella nuova `pszMkDocumentNew` `punkWindowFrame` gerarchia. La gerarchia che esegue il comando Salva con nome chiama questo metodo.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
