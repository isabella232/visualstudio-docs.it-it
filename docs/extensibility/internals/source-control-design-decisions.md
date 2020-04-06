---
title: Decisioni di progettazione del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705251"
---
# <a name="source-control-design-decisions"></a>Decisioni di progettazione relative al controllo del codice sorgente
Le decisioni di progettazione seguenti devono essere prese in considerazione per i progetti durante l'implementazione del controllo del codice sorgente.

## <a name="will-information-be-shared-or-private"></a>Le informazioni saranno condivise o private?
 La decisione di progettazione più importante che è possibile prendere è quali informazioni sono condivisibili e quali sono private. Ad esempio, l'elenco dei file per il progetto è condiviso, ma all'interno di questo elenco di file, alcuni utenti potrebbero voler avere file privati. Le impostazioni del compilatore sono condivise, ma il progetto di avvio è in genere privato. Le impostazioni sono puramente condivise, condivise con una sostituzione o puramente private. Per impostazione predefinita, gli elementi privati, ad esempio i [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]file delle opzioni utente della soluzione (con estensione suo), non vengono archiviati in . Assicurarsi di archiviare tutte le informazioni private in file privati, ad esempio il file con estensione suo, o un file privato specifico creato, ad esempio, un file con estensione csproj.user per Visual Cè o un file con estensione vbproj.user per Visual Basic.

 Questa decisione non è all-inclusive e può essere presa su base articolo per articolo.

## <a name="will-the-project-include-special-files"></a>Il progetto includerà file speciali?
 Un'altra importante decisione di progettazione è se la struttura del progetto utilizza file speciali. I file speciali sono file nascosti che sono alla base dei file visibili in Esplora soluzioni e nelle finestre di dialogo di archiviazione ed estrazione. Se si utilizzano file speciali, attenersi alle seguenti linee guida:

1. Non associare file speciali al nodo radice del progetto, ovvero al file di progetto stesso. Il file di progetto deve essere un singolo file.

2. Quando in un progetto vengono aggiunti, rimossi o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> rinominati file speciali, gli eventi appropriati devono essere generati con il flag impostato che indica che i file sono file speciali. Questi eventi vengono chiamati dall'ambiente in risposta <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> al progetto che chiama i metodi appropriati.

3. Quando il progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> o l'editor richiede un file, i file speciali associati a tale file non vengono estratti automaticamente. Passare i file speciali insieme al file padre. L'ambiente rileverà la relazione tra tutti i file passati e nasconderà in modo appropriato i file speciali nell'interfaccia utente di estrazione.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
