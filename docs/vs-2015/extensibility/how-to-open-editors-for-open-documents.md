---
title: 'Procedura: Aprire gli editor di documenti aperti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a8238ce632f8552b36ccb259af683636732b469
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968251"
---
# <a name="how-to-open-editors-for-open-documents"></a>Procedura: Aprire gli editor per i documenti aperti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prima di una finestra del documento viene aperto un progetto, il progetto prima di tutto necessario determinare se il file è già aperto nella finestra del documento per un altro editor. Il file è possibile aprire in un editor specifico del progetto o uno degli editor standard registrato con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Aprire un Editor specifico del progetto  
 Usare la procedura seguente per aprire un editor specifico del progetto per un file che è già aperto.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Per aprire un editor specifico del progetto per un file aperto  
  
1. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
    Questa chiamata restituisce puntatori alla gerarchia del documento, elemento della gerarchia e cornice della finestra, se appropriato.  
  
2. Se il documento è aperto, il progetto deve verificare se è presente solo un oggetto dati del documento o se è presente anche un oggetto visualizzazione del documento.  
  
   - Se è presente un oggetto visualizzazione del documento e questa visualizzazione è per una gerarchia diversa o un elemento della gerarchia, il progetto utilizza il puntatore alla cornice della finestra della visualizzazione per resurface finestra esistente.  
  
   - Se è presente un oggetto visualizzazione del documento e questa visualizzazione è disponibile per la stessa gerarchia ed elemento di gerarchia, il progetto può aprire una seconda vista se è possibile collegare all'oggetto dati documento sottostante. In caso contrario, il progetto deve utilizzare il puntatore alla cornice della finestra della visualizzazione a resurface finestra esistente.  
  
   - Se esiste l'oggetto dati del documento, solo il progetto deve determinare se l'oggetto dati del documento possono utilizzare per la relativa visualizzazione. Se l'oggetto dati del documento è compatibile, completato i passaggi descritti in [apertura di un Editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).  
  
     Se l'oggetto dati del documento non è compatibile, dovrebbe essere visualizzato un errore all'utente che indica che il file è attualmente in uso. Questo errore deve essere visualizzato solo in casi temporanei, ad esempio quando un file è in fase di compilazione nello stesso momento l'utente sta tentando di aprire il file utilizzando un editor diverso il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor di testo principale. L'editor di testo principale può condividere l'oggetto dati del documento con il compilatore.  
  
3. Se il documento non è aperto perché non esiste un oggetto dati del documento o un oggetto visualizzazione del documento, completare i passaggi descritti in [apertura di un Editor specifico del progetto](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Aprire un Editor Standard  
 Utilizzare la procedura seguente per aprire un editor standard di un file che è già aprire.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Per aprire un editor standard di un file aperto  
  
1.  Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Questo metodo verifica innanzitutto che il documento non è già aperto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Se il documento è già aperto, la finestra dell'editor è riapparire.  
  
2.  Se il documento non è aperto, quindi completare la procedura descritta in [come: Aprire gli editor Standard](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: Apri editor specifici del progetto](../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: Aprire gli editor Standard](../extensibility/how-to-open-standard-editors.md)
