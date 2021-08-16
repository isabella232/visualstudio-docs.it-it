---
title: Decisioni di progettazione del controllo del codice sorgente | Microsoft Docs
description: Informazioni su diverse decisioni di progettazione chiave da prendere in considerazione per i progetti durante l'implementazione del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 79cbc22b16835e0f6c3fa9caa41ac9720c7022d8786520b1baf89d33c3b64948
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275177"
---
# <a name="source-control-design-decisions"></a>Decisioni di progettazione relative al controllo del codice sorgente
Quando si implementa il controllo del codice sorgente, è necessario prendere in considerazione le decisioni di progettazione seguenti per i progetti.

## <a name="will-information-be-shared-or-private"></a>Le informazioni saranno condivise o private?
 La decisione di progettazione più importante da prendere è la condivisione delle informazioni e le informazioni private. Ad esempio, l'elenco dei file per il progetto è condiviso, ma all'interno di questo elenco di file, alcuni utenti potrebbero voler avere file privati. Le impostazioni del compilatore sono condivise, ma il progetto di avvio è in genere privato. Impostazioni sono puramente condivisi, condivisi con un override o puramente privati. Per impostazione predefinita, gli elementi privati, ad esempio i file delle opzioni utente della soluzione (con estensione suo), non vengono archiviati in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] . Assicurarsi di archiviare le informazioni private in file privati, ad esempio il file suo o un file privato specifico creato, ad esempio un file con estensione csproj.user per Visual C# o un file vbproj.user per Visual Basic.

 Questa decisione non è inclusiva e può essere presa elemento per elemento.

## <a name="will-the-project-include-special-files"></a>Il progetto includerà file speciali?
 Un'altra importante decisione di progettazione è se la struttura del progetto usa file speciali. I file speciali sono file nascosti sottostanti ai file visibili in Esplora soluzioni e nelle finestre di dialogo di archiviazione e estrazione. Se si usano file speciali, seguire queste linee guida:

1. Non associare file speciali al nodo radice del progetto, ovvero al file di progetto stesso. Il file di progetto deve essere un singolo file.

2. Quando vengono aggiunti, rimossi o rinominati file speciali in un progetto, gli eventi appropriati devono essere generati con il flag impostato che indica che i <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> file sono file speciali. Questi eventi vengono chiamati dall'ambiente in risposta al progetto che chiama i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> appropriati.

3. Quando il progetto o l'editor chiama per un file, i file <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> speciali associati a tale file non vengono estratti automaticamente. Passare i file speciali in insieme al file padre. L'ambiente rileverà la relazione tra tutti i file passati e nasconderà in modo appropriato i file speciali nell'interfaccia utente di estrazione.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
