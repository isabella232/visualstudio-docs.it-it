---
title: Project Contesto | Microsoft Docs
description: Informazioni su come l Visual Studio IDE usa il contesto del progetto per determinare come eseguire operazioni quando l'utente aggiunge o usa progetti ed elementi di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d4d789a597682ad881dd64f4a12580cd10b6e766
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117852"
---
# <a name="project-context"></a>Contesto di progetto
Quando l'utente aggiunge o usa progetti ed elementi di progetto, l'IDE usa la nozione di contesto del progetto per determinare la modalità di esecuzione delle varie operazioni.

 In genere, i file sono gli oggetti di progetto standard che l'utente crea in modo esplicito selezionando il comando Nuovo **Project** o rende disponibili scegliendo il comando Apri **Project** dal menu **File.** In questi casi, i file vengono creati e aperti nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.

 Alcuni progetti offrono un contesto molto ampio. Ad esempio, il progetto gestisce uno spazio dei nomi a livello di progetto e programmatico o una connessione di database con ambito progetto per data binding. L'utente può spesso aprire file o connessioni di database direttamente usando un particolare oggetto di progetto, ad esempio un elemento di progetto visualizzato in Esplora soluzioni.

 In altri casi, il contesto di progetto di un elemento non viene specificato in modo esplicito. Ad esempio, il contesto di un elemento non è disponibile quando l'utente apre un file selezionando il comando Apri **file** esistente  dal menu **File**  , quando il debugger opera su un file o quando l'utente fa clic sul comando Trova nei file nella finestra di dialogo Trova e sostituisci . Per gestire queste situazioni, l'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> chiama per gestire il processo di ricerca del progetto migliore per aprire un documento.

## <a name="see-also"></a>Vedi anche
- [Priorità di progetto](../../extensibility/internals/project-priority.md)
- [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
