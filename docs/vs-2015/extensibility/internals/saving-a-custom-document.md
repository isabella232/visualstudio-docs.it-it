---
title: Salvataggio di un documento personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5a25cc7f64c50ca088e11cc69a122f97333dfc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529148"
---
# <a name="saving-a-custom-document"></a>Salvataggio di un documento personalizzato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [salvataggio un documento personalizzato](https://docs.microsoft.com/visualstudio/extensibility/internals/saving-a-custom-document).  
  
Gli handle di ambiente il **salvare**, **Salva con nome**, e **Salva tutto** comandi. Quando un utente fa clic **salvare**, **Salva con nome**, **o Salva tutto** nel **File** menu o chiude la soluzione, causando un Salva tutto, quanto segue si verifica.  
  
 ![Salvataggio Editor Customer](../../extensibility/internals/media/private.gif "privato")  
Salvare, Salva e Salva tutto gestione dei comandi per un editor personalizzato  
  
 Questa procedura è descritta nei passaggi seguenti:  
  
1.  Per il **salvare** e **Salva con nome** comandi, nell'ambiente viene usato il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> del servizio per determinare la finestra del documento attivo e in questo modo gli elementi che devono essere salvate. Dopo che è noto che la finestra del documento attivo, l'ambiente Cerca il puntatore di gerarchia e l'identificatore dell'elemento (ID elemento) per il documento nella tabella documenti in esecuzione. Per altre informazioni, vedere [tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md).  
  
     Per il comando Salva tutto, l'ambiente utilizza le informazioni nella tabella documenti in esecuzione per compilare l'elenco di tutti gli elementi da salvare.  
  
2.  Quando la soluzione riceve un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiamata, scorre il set di elementi selezionati (vale a dire le selezioni multiple esposte dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servizio).  
  
3.  Su ogni elemento nella selezione, la soluzione Usa il puntatore di gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodo per determinare se il comando di menu Salva deve essere abilitato. Se uno o più elementi vengono modificati, è abilitato il comando Salva. Se la gerarchia Usa un editor standard, i delegati di gerarchia per l'esecuzione di query modificato lo stato per l'editor chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> (metodo).  
  
4.  Su ogni elemento selezionato è stato modificato, la soluzione Usa il puntatore di gerarchia per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metodo sulle gerarchie appropriate.  
  
     Nel caso di un editor personalizzato, la comunicazione tra l'oggetto dati del documento e il progetto è privata. In questo modo, eventuali problemi di persistenza speciali vengono gestiti tra questi due oggetti.  
  
    > [!NOTE]
    >  Se si implementa il proprio persistenza, accertarsi di chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> metodo per risparmiare tempo. Questo metodo consente di assicurarsi che sia sicuro salvare il file (ad esempio, il file non è in sola lettura).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)

