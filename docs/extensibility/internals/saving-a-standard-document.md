---
title: Salvataggio di un documento standard Documenti Microsoft
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
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705546"
---
# <a name="saving-a-standard-document"></a>Salvataggio di un documento standard
L'ambiente gestisce i comandi Salva, Salva con nome e Salva tutto. Quando un utente seleziona **Salva**, Salva con **nome**o **Salva tutto** dal menu **File** o chiude la soluzione, generando un'istruzione Salva **tutto**, si verifica il processo seguente.

 ![Editor standard](../../extensibility/internals/media/public.gif "Pubblico") Gestione comandi Salva, Salva con nome e Salva tutto per un editor standard

 Questo processo è descritto nei passaggi seguenti:This process is detailed in the following steps:

1. Quando i comandi **Salva** e **Salva con** <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> nome sono selezionati, l'ambiente utilizza il servizio per determinare la finestra del documento attivo e quindi gli elementi da salvare. Una volta nota la finestra del documento attivo, l'ambiente trova il puntatore della gerarchia e l'identificatore di elemento (itemID) per il documento nella tabella dei documenti in esecuzione. Per ulteriori informazioni, vedere [Esecuzione della tabella documenti](../../extensibility/internals/running-document-table.md).

    Quando il comando **Salva tutto** è selezionato, l'ambiente utilizza le informazioni nella tabella dei documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.

2. Quando la soluzione <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> riceve una chiamata, scorre il set di elementi selezionati, ovvero <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> le selezioni multiple esposte dal servizio.

3. Su ogni elemento nella selezione, la soluzione utilizza <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> il puntatore della gerarchia per chiamare il metodo per determinare se il comando di menu **Salva** deve essere abilitato. Se uno o più elementi sono sporchi, il comando **Salva** è abilitato. Se la gerarchia utilizza un editor standard, la gerarchia delega <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> l'esecuzione di query per lo stato dirty all'editor chiamando il metodo .

4. Su ogni elemento selezionato che è dirty, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> soluzione utilizza il puntatore della gerarchia per chiamare il metodo sulle gerarchie appropriate.

    È comune per la gerarchia utilizzare un editor standard per modificare il documento. In questo caso, l'oggetto dati del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> documento per l'editor deve supportare l'interfaccia. Dopo aver <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> ricevuto la chiamata al metodo, il progetto deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> informare l'editor che il documento viene salvato chiamando il metodo sull'oggetto dati del documento. L'editor può consentire all'ambiente di gestire `Query Service` la <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> finestra di dialogo **Salva con** nome, chiamando l'interfaccia . Restituisce un puntatore all'interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> L'editor deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> quindi chiamare il metodo, passando <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> un puntatore `pPersistFile` all'implementazione dell'editor tramite il parametro . L'ambiente esegue quindi l'operazione Salva e fornisce la finestra di dialogo **Salva con** nome per l'editor. L'ambiente richiama quindi l'editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Se l'utente sta tentando di salvare un documento senza titolo(ovvero, un documento precedentemente non salvato), viene effettivamente eseguito un comando Salva con nome.

6. Per il comando Salva con nome, nell'ambiente viene visualizzata la finestra di dialogo Salva con nome, in cui viene richiesto all'utente un nome file.

    Se il nome del file è stato modificato, la gerarchia è responsabile dell'aggiornamento delle informazioni memorizzate nella cache del frame del documento chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).

   Se il comando **Salva con** nome sposta la posizione del documento e la gerarchia è sensibile alla posizione del documento, la gerarchia è responsabile della consegna della proprietà della finestra del documento aperto a un'altra gerarchia. Ad esempio, ciò si verifica se il progetto tiene traccia se il file è un file interno o esterno (File varie) in relazione al progetto. Utilizzare la procedura seguente per modificare la proprietà di un file nel progetto File esterni.

## <a name="changing-file-ownership"></a>Modifica della proprietà dei file

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Per modificare la proprietà del file nel progetto File esterni

1. Servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> query per l'interfaccia.

     Viene restituito <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> un puntatore a.

2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> il`pszMkDocumentNew` `punkWindowFrame`metodo ( , ) per trasferire il documento nella nuova gerarchia. La gerarchia che esegue il comando Salva con nome chiama questo metodo.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
