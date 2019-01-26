---
title: Decisioni di progettazione di controllo di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f47e0bdcf5b8dd3a7c41004ce82fca9f92db509e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936828"
---
# <a name="source-control-design-decisions"></a>Decisioni di progettazione relative al controllo del codice sorgente
Le seguenti decisioni di progettazione devono essere considerate per i progetti durante l'implementazione di controllo del codice sorgente.  
  
## <a name="will-information-be-shared-or-private"></a>Informazioni sarà condiviso o privato?  
 La più importante decisione di progettazione che è possibile rendere è quali informazioni sono condivisibile e What ' s privata. Ad esempio, l'elenco dei file per il progetto è condivisa, ma all'interno dell'elenco di file, alcuni utenti potrebbero essere necessario disporre di file privati. Le impostazioni del compilatore sono condivisi, ma il progetto di avvio è in genere privato. Le impostazioni sono puramente condivisi, condivisi con un override o puramente privato. Per impostazione predefinita, gli elementi privati, ad esempio i file (con estensione suo), delle opzioni utente soluzione non vengono controllati in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Assicurarsi di archiviare informazioni private nel file privati, ad esempio il file con estensione suo, o un file privato specifico, ad esempio, crea una. file csproj per Visual c# o. vbproj per Visual Basic.  
  
 Questa decisione non è gratis e può essere fatta in un singolo elemento per elemento.  
  
## <a name="will-the-project-include-special-files"></a>Il progetto includerà i file speciali?  
 Un'altra importante decisione di progettazione è che la struttura del progetto usi file speciali. File speciali sono i file nascosti sottostanti i file che sono finestre di dialogo di estrazione e visibile in Esplora soluzioni e il check-in. Se si utilizzano file speciali, seguire queste linee guida:  
  
1.  Non associare file speciali con il nodo radice del progetto, vale a dire, con il progetto file stesso. File di progetto deve essere un singolo file.  
  
2.  Quando i file speciali sono aggiunto, rimosso o rinominati in un progetto appropriato <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> eventi devono essere generati con il set di flag che indica i file sono file speciali. Questi eventi vengono chiamati dall'ambiente in risposta al progetto chiamando appropriato <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metodi.  
  
3.  Quando il progetto o l'editor chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> per un file, i file speciali associati a tale file non vengono archiviati automaticamente. Passare i file speciali nell'insieme al file padre. L'ambiente rileverà la relazione tra tutti i file che vengono passati e nascondere in modo appropriato i file speciali nell'interfaccia utente di estrazione.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)