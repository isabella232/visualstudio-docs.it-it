---
title: Supporto di più visualizzazioni documento | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91becc7afb7c236ebe9d6e08c1b8a221cb9f90fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826545"
---
# <a name="supporting-multiple-document-views"></a>Supporto di più visualizzazioni documento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile fornire più di una visualizzazione di un documento tramite la creazione di dati del documento separata e oggetti di visualizzazione di documenti per l'editor. Alcuni casi in cui una visualizzazione del documento aggiuntivo potrebbe essere utile sono:  
  
- Nuovo supporto di finestre: si desidera fornire due o più viste dello stesso tipo, l'editor in modo che un utente che dispone già di una finestra aprire nell'editor è possibile aprire una nuova finestra selezionando il **nuova finestra** dal **finestra** dal menu.  
  
- Formato e il codice consente di visualizzare il supporto: si vuole che l'editor per fornire visualizzazioni di tipi diversi. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], ad esempio, fornisce una visualizzazione form e una visualizzazione del codice.  
  
  Per altre informazioni, vedere la procedura CreateEditorInstance nel file EditorFactory.cs nel progetto editor personalizzato creato dal modello di pacchetto Visual Studio. Per altre informazioni su questo progetto, vedere [procedura dettagliata: creazione di un Editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>La sincronizzazione delle viste  
 Quando si implementano visualizzazioni multiple, l'oggetto dati del documento è responsabilità di conservare tutte le visualizzazioni sincronizzate con i dati. È possibile usare l'evento di gestione delle interfacce su <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> per sincronizzare più visualizzazioni con i dati.  
  
 Se non si usa il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto per sincronizzare più visualizzazioni, è necessario implementare il proprio sistema di eventi per gestire le modifiche apportate all'oggetto dati del documento. È possibile usare diversi livelli di granularità per mantenere aggiornati più viste. Con un'impostazione di massima granularità, durante la digitazione in un'unica visualizzazione le altre visualizzazioni vengono aggiornate immediatamente. Con una granularità minima, non altre visualizzazioni vengono aggiornate fino a quando non vengono attivati.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Determinare se i dati del documento è già aperto  
 La tabella documenti in esecuzione (RDT) nell'ambiente di sviluppo integrato (IDE) consente di verificare se i dati per un documento sono già aperti, come illustrato nel diagramma seguente.  
  
 ![Immagine di DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Visualizzazioni multiple  
  
 Per impostazione predefinita, ogni vista (oggetto visualizzazione del documento) viene contenuta in una proprio cornice della finestra (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Come già notato, tuttavia, dati documento possono essere visualizzati in visualizzazioni multiple. A tale scopo, Visual Studio verifica RDT per determinare se il documento in questione è già aperto in un editor. Quando l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> per creare l'editor, un valore non NULL restituito nel `punkDocDataExisting` parametro indica che il documento è già aperto in un altro editor. Per altre informazioni su come visualizzare le funzioni, RDT [tabella documenti in esecuzione](../extensibility/internals/running-document-table.md).  
  
 Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementazione, esaminare l'oggetto dati del documento restituito nella `punkDocDataExisting` per determinare se i dati del documento sono appropriati per l'editor. (Ad esempio, solo i dati HTML devono essere visualizzati da un editor HTML.) Se è appropriato, quindi la factory dell'editor deve fornire una seconda vista per i dati. Se il `punkDocDataExisting` parametro non `NULL`, è possibile sia che l'oggetto dati del documento è aperto in un altro editor, o, più probabile, che i dati del documento sono già aperti in una vista diversa con l'editor stesso. Se i dati del documento sono aperti in un editor diverso che non supporta la factory dell'editor, Visual Studio non riesce aprire la factory dell'editor. Per altre informazioni, vedere [procedura: collegare visualizzazioni ai dati documento](../extensibility/how-to-attach-views-to-document-data.md).

