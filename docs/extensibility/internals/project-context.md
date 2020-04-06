---
title: Contesto del progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706590"
---
# <a name="project-context"></a>Contesto di progetto
Quando l'utente aggiunge o utilizza progetti ed elementi di progetto, l'IDE utilizza la nozione di contesto del progetto per determinare come devono essere eseguite le varie operazioni.

 In genere, i file sono gli oggetti di progetto standard che l'utente crea in modo esplicito selezionando il **nuovo progetto** comando o rende disponibile selezionando il **Apri progetto** comando dal **File** menu. In questi casi, i file vengono creati e aperti nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.

 Alcuni progetti forniscono un contesto molto ricco. Ad esempio, il progetto gestisce uno spazio dei nomi con ambito di progetto, uno spazio dei nomi a livello di codice o una connessione al database con ambito di progetto per l'associazione dati. L'utente può spesso aprire file o connessioni di database direttamente utilizzando un oggetto di progetto specifico, ad esempio un elemento di progetto visualizzato in Esplora soluzioni.

 In altri casi, il contesto di progetto di un elemento non è specificato in modo esplicito. Ad esempio, il contesto di un elemento non è disponibile quando l'utente apre un file selezionando il comando **Apri file esistente** dal menu **File** , quando il debugger opera su un file o quando l'utente fa clic sul comando Trova **nei file** nella finestra di dialogo Trova **e sostituisci** . Per gestire queste situazioni, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> l'IDE chiama per gestire il processo di trovare il progetto migliore per aprire un documento.

## <a name="see-also"></a>Vedere anche
- [Priorità di progetto](../../extensibility/internals/project-priority.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
