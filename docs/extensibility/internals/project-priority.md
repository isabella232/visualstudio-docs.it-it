---
title: Priorità del progetto Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706425"
---
# <a name="project-priority"></a>Priorità di progetto
Un elemento di progetto è in genere un membro di un solo progetto nella soluzione. Pertanto, l'IDE può determinare facilmente quale progetto viene utilizzato per aprire l'elemento. Tuttavia, se un elemento è un membro di più di un progetto, l'IDE utilizza uno schema di priorità per determinare il progetto migliore per l'apertura dell'elemento.

 L'elenco seguente mostra lo schema di priorità del progetto:

- L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> chiama il metodo per ogni progetto nella soluzione per determinare se il documento è un membro di tale progetto.

- Se il documento è un membro del progetto, il progetto risponde con una priorità che il progetto assegna in base alla gestione del documento. Ad esempio, un progetto di linguaggio risponde con una priorità alta per i file di origine del linguaggio, ma risponde con una priorità inferiore per un tipo di file non riconosciuto che non viene utilizzato come parte del processo di compilazione.

- Anche i progetti che forniscono editor o finestre di progettazione personalizzati e specifici del progetto per un documento ricevono una priorità elevata.

- L'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> fornisce i valori di priorità del documento.

- Al progetto che specifica la priorità più alta viene assegnato il contesto per aprire il documento. Se due progetti restituiscono valori di priorità uguali, è preferibile il progetto attivo. Se nessun progetto nella soluzione risponde che è possibile aprire il documento, l'IDE inserisce il documento nel progetto file esterni. Per ulteriori informazioni, vedere [Progetto File esterni](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Vedere anche
- [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)
- [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
