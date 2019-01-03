---
title: Contesto del progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92a0f875e51b0cb9ff968bf93b8a0877b14149c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990149"
---
# <a name="project-context"></a>Contesto di progetto
Quando l'utente aggiunge o si funziona con i progetti ed elementi del progetto, l'IDE Usa il concetto di contesto del progetto per determinare come le varie operazioni devono essere eseguite.  
  
 In genere, i file sono gli oggetti di progetto standard che l'utente crea in modo esplicito selezionando il **nuovo progetto** comando o rende disponibile selezionando il **aprire il progetto** comando il  **File** menu. In questi casi, i file vengono creati e aperti nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.  
  
 Alcuni progetti forniscono un contesto molto avanzato. Ad esempio, il progetto gestisce una connessione di database con ambito di progetto per il data binding o dello spazio dei nomi con ambito di progetto a livello di codice. L'utente può spesso aprire i file o le connessioni al database direttamente tramite un oggetto particolare progetto, ad esempio un elemento del progetto visualizzato in Esplora soluzioni.  
  
 In altri momenti, il contesto del progetto di un elemento non è specificato in modo esplicito. Ad esempio, il contesto di un elemento non è disponibile quando l'utente apre un file, selezionare il **aprire il File esistente** comando il **File** menu, durante il debug viene eseguito in un file o quando l'utente fa clic di **Cerca nei file** comando le **Trova e sostituisci** nella finestra di dialogo. Per gestire queste situazioni, le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> per gestire il processo di individuazione il migliore progetto per aprire un documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Priorità del progetto](../../extensibility/internals/project-priority.md)   
 [Aggiunta di modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)