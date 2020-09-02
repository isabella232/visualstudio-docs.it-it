---
title: Persistenza progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abbcc1fc1048866ef790a4b6779ed15ef80a9be1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429522"
---
# <a name="project-persistence"></a>Salvataggio permanente dei progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La persistenza è una considerazione della progettazione chiave per il progetto. La maggior parte dei progetti utilizza gli elementi del progetto che rappresentano i file; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta inoltre progetti i cui dati non sono basati su file. È necessario che i file di proprietà del progetto e il file di progetto siano salvati in permanenza. L'IDE indica al progetto di salvare se stesso o un elemento del progetto.  
  
 I modelli per i progetti vengono passati alla factory del progetto. I modelli devono supportare l'inizializzazione di tutti gli elementi del progetto in base ai requisiti del tipo di progetto specifico. Questi modelli possono essere salvati in un secondo momento come file di progetto e gestiti dall'IDE tramite la soluzione. Per altre informazioni, vedere [Creating Project Instances by using Project factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) and [Solutions](../../extensibility/internals/solutions-overview.md).  
  
 Gli elementi del progetto possono essere basati su file o non basati su file:  
  
- Gli elementi basati su file possono essere locali o remoti. Nei progetti Web in C#, ad esempio, le connessioni ai file in un sistema remoto vengono mantenute localmente, mentre i file stessi vengono mantenuti nel sistema remoto.  
  
- Gli elementi non basati su file possono salvare elementi in un database o in un repository.  
  
## <a name="commit-models"></a>Esegui commit modelli  
 Dopo aver deciso dove si trovano gli elementi del progetto, è necessario scegliere il modello di commit appropriato. Ad esempio, in un modello basato su file con file locali, ogni progetto può essere salvato in modo autonomo. In un modello di repository è possibile salvare più elementi in una transazione. Per altre informazioni, vedere [decisioni di progettazione dei tipi di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
 Per determinare le estensioni dei nomi di file, i progetti implementano l' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaccia, che fornisce informazioni che consentono al client di un oggetto di implementare la finestra di dialogo **Salva con** nome, ovvero di compilare l'elenco a discesa **Salva come tipo** e gestire l'estensione del nome file iniziale.  
  
 L'IDE chiama l' `IPersistFileFormat` interfaccia nel progetto per indicare che il progetto deve salvare in modo permanente gli elementi del progetto nel modo appropriato. Pertanto, l'oggetto è proprietario di tutti gli aspetti del relativo file e del relativo formato. Include il nome del formato dell'oggetto.  
  
 Nel caso in cui gli elementi non siano file, `IPersistFileFormat` rimane comunque il modo in cui gli elementi non basati su file sono persistenti. Anche i file di progetto, ad esempio i file con estensione vbp per [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] i progetti o i file VCPROJ per i [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] progetti, devono essere salvati in modo permanente.  
  
 Per le azioni di salvataggio, l'IDE esamina la tabella documenti in esecuzione (RDT) e la gerarchia passa i comandi alle <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfacce e. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> metodo viene implementato per determinare se l'elemento è stato modificato. Se l'elemento ha, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> metodo viene implementato per salvare l'elemento modificato.  
  
 I metodi sull' `IVsPersistHierarchyItem2` interfaccia vengono usati per determinare se un elemento può essere ricaricato e, se l'elemento può essere, per ricaricarlo. Inoltre, è <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> possibile implementare il metodo per fare in modo che gli elementi modificati vengano eliminati senza essere salvati.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
