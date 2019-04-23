---
title: Priorità di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b012136c30f72cfdddadfc1a370ed76f567afffd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079671"
---
# <a name="project-priority"></a>Priorità di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In genere, un elemento del progetto è un membro di un solo progetto nella soluzione. Di conseguenza, l'IDE di può facilmente determinare quale progetto viene utilizzato per aprire l'elemento. Tuttavia, se un elemento è un membro di più di un progetto, l'IDE usa uno schema di priorità per determinare il migliore progetto per aprire l'elemento.  
  
 Nell'elenco seguente viene illustrato lo schema di priorità di progetto:  
  
- Le chiamate dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metodo per ogni progetto nella soluzione per determinare se il documento è un membro di tale progetto.  
  
- Se il documento è un membro del progetto, il progetto risponde con una priorità di progetto viene assegnata in base alla relativa funzionalità di gestione di tale documento. Ad esempio, un progetto in linguaggio risponde con una priorità assoluta per i file di origine della lingua ma risponde con una priorità più bassa per un tipo di file non riconosciuto che non viene usato come parte del processo di compilazione.  
  
- I progetti che forniscono gli editor personalizzati, specifico del progetto o le finestre di progettazione per un documento ricevono anche una priorità alta.  
  
- Il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione fornisce valori di priorità dei documenti.  
  
- Il progetto che specifica la priorità più elevata viene fornito il contesto per aprire il documento. Se due progetti di restituiscono i valori di uguale priorità, il progetto attivo è preferito. Se nessun progetto nella soluzione risponde che è possibile aprire il documento, l'IDE inserisce il documento nel progetto file esterni. Per altre informazioni, vedere [progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Progetto file esterni](../../extensibility/internals/miscellaneous-files-project.md)   
 [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
