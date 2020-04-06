---
title: Persistenza del progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706464"
---
# <a name="project-persistence"></a>Salvataggio permanente dei progetti
La persistenza è una considerazione di progettazione chiave per il progetto. La maggior parte dei progetti utilizza elementi di progetto che rappresentano i file; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta anche progetti i cui dati non sono basati su file. Sia i file di proprietà del progetto che il file di progetto devono essere resi persistenti. L'IDE indica al progetto di salvare se stesso o un elemento di progetto.

 I modelli per i progetti vengono passati alla factory del progetto. I modelli devono supportare l'inizializzazione di tutti gli elementi di progetto in base ai requisiti del tipo di progetto specifico. Questi modelli possono essere salvati in un secondo momento come file di progetto e gestiti dall'IDE tramite la soluzione. Per ulteriori informazioni, vedere Creazione di istanze di [progetto tramite soluzioni](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) [e](../../extensibility/internals/solutions-overview.md)factory di progetto .

 Gli elementi di progetto possono essere basati su file o non basati su file:Project items can be file-based or non-file-based:

- Gli elementi basati su file possono essere locali o remoti. Nei progetti Web in C, ad esempio, le connessioni ai file in un sistema remoto vengono mantenute localmente, mentre i file stessi vengono mantenuti nel sistema remoto.

- Gli elementi non basati su file possono salvare gli elementi in un database o in un repository.

## <a name="commit-models"></a>Modelli di commitCommit Models
 Dopo aver deciso dove si trovano gli elementi di progetto, è necessario scegliere il modello di commit appropriato. Ad esempio, in un modello basato su file con file locali, ogni progetto può essere salvato in modo autonomo. In un modello di repository, è possibile salvare più elementi in una transazione. Per ulteriori informazioni, consultate [Decisioni di progettazione dei](../../extensibility/internals/project-type-design-decisions.md)tipi di progetto .

 Per determinare le estensioni <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> di file, i progetti implementano l'interfaccia, che fornisce informazioni che consentono al client di un oggetto di implementare la finestra di dialogo **Salva con** nome, ovvero di compilare l'elenco a discesa **Tipo** file e gestire l'estensione di file iniziale.

 L'IDE `IPersistFileFormat` chiama l'interfaccia sul progetto per indicare che il progetto deve rendere persistenti i relativi elementi di progetto in base alle esigenze. Pertanto, l'oggetto possiede tutti gli aspetti del relativo file e formato. Ciò include il nome del formato dell'oggetto.

 Nel caso in cui gli `IPersistFileFormat` elementi non sono file, è ancora come gli elementi non basati su file vengono resi persistenti. Anche i file di progetto, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ad esempio i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] file con estensione vbp per i progetti o i file con estensione vcproj per i progetti, devono essere mantenuti.

 Per le azioni di salvataggio, l'IDE esamina la tabella documenti in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> esecuzione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> (RDT) e la gerarchia passa i comandi alle interfacce e . Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> metodo viene implementato per determinare se l'elemento è stato modificato. Se l'elemento <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> ha, il metodo viene implementato per salvare l'elemento modificato.

 I metodi `IVsPersistHierarchyItem2` sull'interfaccia vengono utilizzati per determinare se un elemento può essere ricaricato e, se l'elemento può essere, per ricaricarlo. Inoltre, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> metodo può essere implementato per fare in modo che gli elementi modificati vengano eliminati senza essere salvati.

## <a name="see-also"></a>Vedere anche
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
