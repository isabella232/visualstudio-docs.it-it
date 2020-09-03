---
title: Priorità progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706425"
---
# <a name="project-priority"></a>Priorità di progetto
Un elemento del progetto è in genere un membro di un solo progetto nella soluzione. Pertanto, l'IDE può determinare facilmente quale progetto viene utilizzato per aprire l'elemento. Tuttavia, se un elemento è un membro di più di un progetto, l'IDE usa uno schema di priorità per determinare il progetto migliore per l'apertura dell'elemento.

 L'elenco seguente mostra lo schema di priorità del progetto:

- L'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metodo per ogni progetto nella soluzione per determinare se il documento è un membro di tale progetto.

- Se il documento è un membro del progetto, il progetto risponde con una priorità assegnata dal progetto in base alla relativa gestione del documento. Ad esempio, un progetto di linguaggio risponde con una priorità alta per i file di origine della lingua, ma risponde con una priorità più bassa per un tipo di file non riconosciuto che non viene usato come parte del processo di compilazione.

- I progetti che forniscono editor o finestre di progettazione personalizzate, specifici del progetto per un documento ricevono anche una priorità alta.

- L' <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione fornisce i valori di priorità del documento.

- Al progetto che specifica la priorità più alta viene assegnato il contesto per l'apertura del documento. Se due progetti restituiscono valori di priorità uguali, è preferibile il progetto attivo. Se nessun progetto nella soluzione risponde che è in grado di aprire il documento, l'IDE inserisce il documento nel progetto di file esterni. Per altre informazioni, vedere [progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Vedere anche
- [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)
- [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
