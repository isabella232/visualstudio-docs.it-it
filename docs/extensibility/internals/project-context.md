---
title: Contesto progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8afa595a264f218fcc20f18de1c261a9ead6e030
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725777"
---
# <a name="project-context"></a>Contesto di progetto
Quando l'utente aggiunge o lavora con progetti ed elementi di progetto, l'IDE usa la nozione di contesto del progetto per determinare il modo in cui devono essere eseguite le varie operazioni.

 In genere, i file sono gli oggetti di progetto standard creati dall'utente in modo esplicito selezionando il comando **nuovo progetto** o rende disponibili selezionando il comando **Apri progetto** dal menu **file** . In questi casi, i file vengono creati e aperti nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.

 Alcuni progetti forniscono un contesto molto ricco. Il progetto, ad esempio, gestisce una connessione a un database con ambito di progetto o di progetto per data binding. L'utente può aprire spesso i file o le connessioni al database direttamente usando un determinato oggetto progetto, ad esempio un elemento del progetto visualizzato in Esplora soluzioni.

 In altri casi, il contesto del progetto di un elemento non viene specificato in modo esplicito. Ad esempio, il contesto di un elemento non è disponibile quando l'utente apre un file selezionando il comando **Apri file esistente** dal menu **file** , quando il debugger opera su un file o quando l'utente fa clic sul comando **Cerca nei file** nel  **Finestra di dialogo Trova e Sostituisci** . Per gestire queste situazioni, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> per gestire il processo di ricerca del progetto migliore per l'apertura di un documento.

## <a name="see-also"></a>Vedere anche
- [Priorità di progetto](../../extensibility/internals/project-priority.md)
- [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)