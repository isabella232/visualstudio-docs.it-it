---
title: Project Persistenza | Microsoft Docs
description: Informazioni sulla persistenza nella progettazione del progetto, incluso l'uso di IPersistFileFormat per rendere persistenti gli oggetti di progetto sia file che non basati su file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 19c2da562a3f9a50c9dc4aa56cf095df9d6da285aa482b5268d3ba79a955ff98
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359286"
---
# <a name="project-persistence"></a>Salvataggio permanente dei progetti
La persistenza è una considerazione di progettazione chiave per il progetto. La maggior parte dei progetti usa elementi di progetto che rappresentano i file. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta anche i progetti i cui dati non sono basati su file. Sia i file di proprietà del progetto che il file di progetto devono essere resi persistenti. L'IDE indica al progetto di salvare se stesso o un elemento di progetto.

 I modelli per i progetti vengono passati alla factory del progetto. I modelli devono supportare l'inizializzazione di tutti gli elementi di progetto in base ai requisiti del tipo di progetto specifico. Questi modelli possono essere salvati in un secondo momento come file di progetto e gestiti dall'IDE tramite la soluzione . Per altre informazioni, vedere [Creazione di istanze Project tramite Project factory e](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) [soluzioni](../../extensibility/internals/solutions-overview.md).

 Project elementi possono essere basati su file o non basati su file:

- Gli elementi basati su file possono essere locali o remoti. Nei progetti Web in C#, ad esempio, le connessioni ai file in un sistema remoto vengono mantenute in locale, mentre i file stessi vengono mantenuti nel sistema remoto.

- Gli elementi non basati su file possono salvare gli elementi in un database o in un repository.

## <a name="commit-models"></a>Eseguire il commit di modelli
 Dopo aver deciso dove si trovano gli elementi del progetto, è necessario scegliere il modello di commit appropriato. Ad esempio, in un modello basato su file con file locali, ogni progetto può essere salvato in modo autonomo. In un modello di repository è possibile salvare più elementi in una transazione. Per altre informazioni, vedere Prendere decisioni [Project di progettazione dei tipi.](../../extensibility/internals/project-type-design-decisions.md)

 Per determinare le estensioni di file, i progetti implementano l'interfaccia , che fornisce informazioni che consentono al client di un oggetto di implementare la finestra di dialogo Salva con nome, ovvero per compilare l'elenco a discesa Tipo file e gestire l'estensione iniziale <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> del nome file.  

 L'IDE chiama `IPersistFileFormat` l'interfaccia sul progetto per indicare che il progetto deve rendere persistenti i relativi elementi di progetto in base alle esigenze. Pertanto, l'oggetto è proprietario di tutti gli aspetti del file e del formato. Include il nome del formato dell'oggetto .

 Nel caso in cui gli elementi non siano file, è comunque possibile rendere persistenti gli elementi non basati `IPersistFileFormat` su file. Project anche i file con estensione vbp per i progetti o i file vcproj per i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetti devono essere resi [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] persistenti.

 Per le azioni di salvataggio, l'IDE esamina la tabella del documento in esecuzione (RDT) e la gerarchia passa i comandi alle <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfacce e . Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> metodo viene implementato per determinare se l'elemento è stato modificato. Se l'elemento dispone di , <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> il metodo viene implementato per salvare l'elemento modificato.

 I metodi nell'interfaccia vengono usati per determinare se un elemento può essere ricaricato e, se l'elemento può `IVsPersistHierarchyItem2` essere, ricaricarlo. Inoltre, il metodo può essere implementato per fare in modo che gli elementi modificati <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> vengano eliminati senza essere salvati.

## <a name="see-also"></a>Vedi anche
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
