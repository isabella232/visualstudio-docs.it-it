---
title: Persistenza progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a95c919de9b87ed1782cbdcb029efbf191958f5a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725455"
---
# <a name="project-persistence"></a>Salvataggio permanente dei progetti
La persistenza è una considerazione della progettazione chiave per il progetto. La maggior parte dei progetti utilizza gli elementi del progetto che rappresentano i file;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta inoltre progetti i cui dati non sono basati su file. È necessario che i file di proprietà del progetto e il file di progetto siano salvati in permanenza. L'IDE indica al progetto di salvare se stesso o un elemento del progetto.

 I modelli per i progetti vengono passati alla factory del progetto. I modelli devono supportare l'inizializzazione di tutti gli elementi del progetto in base ai requisiti del tipo di progetto specifico. Questi modelli possono essere salvati in un secondo momento come file di progetto e gestiti dall'IDE tramite la soluzione. Per altre informazioni, vedere [Creating Project Instances by using Project factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) and [Solutions](../../extensibility/internals/solutions-overview.md).

 Gli elementi del progetto possono essere basati su file o non basati su file:

- Gli elementi basati su file possono essere locali o remoti. Nei progetti Web in C#, ad esempio, le connessioni ai file in un sistema remoto vengono mantenute localmente, mentre i file stessi vengono mantenuti nel sistema remoto.

- Gli elementi non basati su file possono salvare elementi in un database o in un repository.

## <a name="commit-models"></a>Esegui commit modelli
 Dopo aver deciso dove si trovano gli elementi del progetto, è necessario scegliere il modello di commit appropriato. Ad esempio, in un modello basato su file con file locali, ogni progetto può essere salvato in modo autonomo. In un modello di repository è possibile salvare più elementi in una transazione. Per altre informazioni, vedere [decisioni di progettazione dei tipi di progetto](../../extensibility/internals/project-type-design-decisions.md).

 Per determinare le estensioni di file, i progetti implementano l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>, che fornisce informazioni che consentono al client di un oggetto di implementare la finestra di dialogo **Salva con** nome, ovvero di compilare l'elenco a discesa **Salva come tipo** e gestire il estensione del nome file iniziale.

 L'IDE chiama l'interfaccia `IPersistFileFormat` nel progetto per indicare che il progetto deve salvare in modo permanente gli elementi del progetto nel modo appropriato. Pertanto, l'oggetto è proprietario di tutti gli aspetti del relativo file e del relativo formato. Include il nome del formato dell'oggetto.

 Nel caso in cui gli elementi non siano file, `IPersistFileFormat` è ancora il modo in cui gli elementi non basati su file sono persistenti. Anche i file di progetto, ad esempio i file con estensione vbp per i progetti [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o i file VCPROJ per i progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], devono essere salvati in modo permanente.

 Per le azioni di salvataggio, l'IDE esamina la tabella documenti in esecuzione (RDT) e la gerarchia passa i comandi alla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> e alle interfacce <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>. Viene implementato il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> per determinare se l'elemento è stato modificato. Se l'elemento ha, viene implementato il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> per salvare l'elemento modificato.

 I metodi sull'interfaccia `IVsPersistHierarchyItem2` vengono usati per determinare se un elemento può essere ricaricato e, se l'elemento può essere, per ricaricarlo. Inoltre, è possibile implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> per far sì che gli elementi modificati vengano eliminati senza essere salvati.

## <a name="see-also"></a>Vedere anche
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)