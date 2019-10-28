---
title: Decisioni di progettazione del controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a7c8a902520323f548a7dd77a84b07a56bfc9a0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723608"
---
# <a name="source-control-design-decisions"></a>Decisioni di progettazione relative al controllo del codice sorgente
Quando si implementa il controllo del codice sorgente, è necessario considerare le seguenti decisioni di progettazione per i progetti.

## <a name="will-information-be-shared-or-private"></a>Le informazioni saranno condivise o private?
 La decisione di progettazione più importante che è possibile prendere è che le informazioni sono condivisibili e che cosa è privato. Ad esempio, l'elenco di file per il progetto è condiviso, ma in questo elenco di file alcuni utenti potrebbero voler avere file privati. Le impostazioni del compilatore sono condivise, ma il progetto di avvio è generalmente privato. Le impostazioni sono puramente condivise, condivise con una sostituzione o esclusivamente private. Per impostazione predefinita, gli elementi privati, ad esempio i file delle opzioni utente della soluzione (. suo), non vengono archiviati in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Assicurarsi di archiviare le informazioni private in file privati, ad esempio il file con estensione suo, oppure un file privato specifico creato, ad esempio un file con estensione csproj. User per un C# file Visual o vbproj. user per Visual Basic.

 Questa decisione non è all-inclusive e può essere eseguita in base a un elemento.

## <a name="will-the-project-include-special-files"></a>Il progetto includerà file speciali?
 Un'altra importante decisione di progettazione consiste nel fatto che la struttura del progetto usi file speciali. I file speciali sono file nascosti sottostanti ai file visibili in Esplora soluzioni e nelle finestre di dialogo Archivia e Estrai. Se si usano file speciali, attenersi alle seguenti linee guida:

1. Non associare file speciali al nodo radice del progetto, ovvero con il file di progetto stesso. Il file di progetto deve essere un singolo file.

2. Quando i file speciali vengono aggiunti, rimossi o rinominati in un progetto, è necessario che vengano generati gli eventi <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> appropriati con il flag impostato che indica che i file sono file speciali. Questi eventi vengono chiamati dall'ambiente in risposta al progetto che chiama i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> appropriati.

3. Quando il progetto o l'editor chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> per un file, i file speciali associati al file non vengono estratti automaticamente. Passare i file speciali in insieme al file padre. L'ambiente rileverà la relazione tra tutti i file passati e nasconderà in modo appropriato i file speciali nell'interfaccia utente di estrazione.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)