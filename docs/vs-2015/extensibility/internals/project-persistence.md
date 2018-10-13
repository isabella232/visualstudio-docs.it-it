---
title: Persistenza del progetto | Microsoft Docs
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
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 068f919ae0717158220712bfe010c58cd401d5d1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177108"
---
# <a name="project-persistence"></a>Salvataggio permanente dei progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La persistenza è una considerazione di progettazione chiave per il progetto. La maggior parte dei progetti usano elementi di progetto che rappresentano file; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta anche progetti i cui dati sono non basate su file. Entrambi i file di proprietà del progetto e il file di progetto devono essere persistente. L'IDE indica il progetto per salvare se stesso o un elemento del progetto.  
  
 Modelli per i progetti vengono passati alla factory del progetto. I modelli devono supportare l'inizializzazione di tutti gli elementi di progetto in base ai requisiti del tipo di progetto specifico. Questi modelli in un secondo momento possono essere salvati come file di progetto e gestiti dall'IDE tramite la soluzione. Per altre informazioni, vedere [creazione di istanze da usando progetto le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) e [soluzioni](../../extensibility/internals/solutions.md).  
  
 Elementi di progetto possono essere basata su file o non basate su file:  
  
-   Gli elementi basati su file possono essere locale o remoto. Nei progetti Web nel linguaggio c#, ad esempio, le connessioni ai file in un sistema remoto vengono mantenuti in locale, mentre gli stessi file persistono nel sistema remoto.  
  
-   Elementi basati su file non è possono salvare gli elementi di un database o nell'archivio.  
  
## <a name="commit-models"></a>Eseguire il commit di modelli  
 Dopo avere deciso in cui si trovano gli elementi del progetto, è necessario scegliere il modello appropriato di commit. Ad esempio, in un modello basato su file con file locali, ogni progetto può essere salvato in modo autonomo. In un modello di repository, è possibile salvare più elementi in un'unica transazione. Per altre informazioni, vedere [decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
 Per determinare le estensioni di file, progetti di implementano il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaccia che fornisce informazioni che consentono al client di un oggetto di implementare il **Salva con nome** nella finestra di dialogo, ovvero, ovvero per riempire il **Salva con nome**  discesa elencare e gestire l'estensione del nome file iniziale.  
  
 Le chiamate dell'IDE di `IPersistFileFormat` interfaccia nel progetto per indicare che il progetto deve essere mantenuto un progetto elementi di base alle esigenze. Pertanto, l'oggetto possiede tutti gli aspetti del relativo file e del formato. Ciò include il nome del formato dell'oggetto.  
  
 Nel caso in cui gli elementi non sono file, `IPersistFileFormat` è comunque la modalità non-basate su file gli elementi sono persistenti. File di progetto, ad esempio file vbp per [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] progetti o con estensione vcproj file per [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] progetti, deve anche essere salvati in modo permanente.  
  
 Per salvare le azioni, l'IDE esamina la tabella documenti in esecuzione (RDT) e la gerarchia passa i comandi per la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfacce. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> metodo è implementato per determinare se l'elemento è stato modificato. Se l'elemento include, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> metodo è implementato per salvare l'elemento modificato.  
  
 I metodi sul `IVsPersistHierarchyItem2` interfaccia vengono utilizzate per determinare se un elemento può essere ricaricato e, se l'elemento può essere, per ricaricarlo. Inoltre, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> metodo può essere implementato per generare gli elementi modificati essere eliminato senza essere salvato.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

