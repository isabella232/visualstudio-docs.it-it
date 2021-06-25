---
title: Priorità progetto | Microsoft Docs
description: Informazioni sullo schema di priorità utilizzato dall'IDE di Visual Studio determinare il progetto migliore per l'apertura di un elemento se l'elemento è membro di più di un progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ac0556e63b25f0f2a0df399cb23d5e2e9473008
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899641"
---
# <a name="project-priority"></a>Priorità di progetto
Un elemento di progetto è in genere membro di un solo progetto nella soluzione. Pertanto, l'IDE può determinare facilmente quale progetto viene usato per aprire l'elemento. Tuttavia, se un elemento è membro di più di un progetto, l'IDE usa uno schema di priorità per determinare il progetto migliore per l'apertura dell'elemento.

 L'elenco seguente mostra lo schema di priorità del progetto:

- L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> chiama il metodo per ogni progetto nella soluzione per determinare se il documento è membro di tale progetto.

- Se il documento è un membro del progetto, il progetto risponde con una priorità assegnata dal progetto in base alla gestione del documento. Ad esempio, un progetto di linguaggio risponde con una priorità elevata per i file di origine del linguaggio, ma risponde con una priorità più bassa per un tipo di file non riconosciuto che non viene usato come parte del processo di compilazione.

- Anche i progetti che forniscono editor o finestre di progettazione personalizzati specifici del progetto per un documento ricevono una priorità alta.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>L'enumerazione fornisce i valori di priorità del documento.

- Al progetto che specifica la priorità più alta viene assegnato il contesto per aprire il documento. Se due progetti restituiscono valori di priorità uguali, è preferibile il progetto attivo. Se nessun progetto nella soluzione risponde che può aprire il documento, l'IDE inserisce il documento nel progetto File esterni. Per altre informazioni, vedere Progetto di [file esterni.](../../extensibility/internals/miscellaneous-files-project.md)

## <a name="see-also"></a>Vedere anche
- [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)
- [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
