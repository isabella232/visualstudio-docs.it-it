---
title: Contesto progetto | Microsoft Docs
description: Informazioni su come l'IDE di Visual Studio usa il contesto del progetto per determinare come eseguire le operazioni quando l'utente aggiunge o utilizza progetti ed elementi di progetto.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bc4234481023592595de2df482d5ff6c2227a95e
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877663"
---
# <a name="project-context"></a>Contesto di progetto
Quando l'utente aggiunge o lavora con progetti ed elementi di progetto, l'IDE usa la nozione di contesto del progetto per determinare il modo in cui devono essere eseguite le varie operazioni.

 In genere, i file sono gli oggetti di progetto standard creati dall'utente in modo esplicito selezionando il comando **nuovo progetto** o rende disponibili selezionando il comando **Apri progetto** dal menu **file** . In questi casi, i file vengono creati e aperti nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.

 Alcuni progetti forniscono un contesto molto ricco. Il progetto, ad esempio, gestisce una connessione a un database con ambito di progetto o di progetto per data binding. L'utente può aprire spesso i file o le connessioni al database direttamente usando un determinato oggetto progetto, ad esempio un elemento del progetto visualizzato in Esplora soluzioni.

 In altri casi, il contesto del progetto di un elemento non viene specificato in modo esplicito. Il contesto di un elemento, ad esempio, non è disponibile quando l'utente apre un file selezionando il comando **Apri file esistente** dal menu **file** , quando il debugger opera su un file o quando l'utente fa clic sul comando **Cerca nei file** nella finestra di dialogo **trova e Sostituisci** . Per gestire queste situazioni, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> per gestire il processo di ricerca del progetto migliore per l'apertura di un documento.

## <a name="see-also"></a>Vedi anche
- [Priorità di progetto](../../extensibility/internals/project-priority.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
