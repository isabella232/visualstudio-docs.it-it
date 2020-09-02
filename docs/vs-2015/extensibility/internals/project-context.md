---
title: Contesto progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4ee4da5fdea63cf1bdd33554c72f6dac30d0334
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429938"
---
# <a name="project-context"></a>Contesto di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando l'utente aggiunge o lavora con progetti ed elementi di progetto, l'IDE usa la nozione di contesto del progetto per determinare il modo in cui devono essere eseguite le varie operazioni.  
  
 In genere, i file sono gli oggetti di progetto standard creati dall'utente in modo esplicito selezionando il comando **nuovo progetto** o rende disponibili selezionando il comando **Apri progetto** dal menu **file** . In questi casi, i file vengono creati e aperti nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.  
  
 Alcuni progetti forniscono un contesto molto ricco. Il progetto, ad esempio, gestisce una connessione a un database con ambito di progetto o di progetto per data binding. L'utente può aprire spesso i file o le connessioni al database direttamente usando un determinato oggetto progetto, ad esempio un elemento del progetto visualizzato in Esplora soluzioni.  
  
 In altri casi, il contesto del progetto di un elemento non viene specificato in modo esplicito. Il contesto di un elemento, ad esempio, non è disponibile quando l'utente apre un file selezionando il comando **Apri file esistente** dal menu **file** , quando il debugger opera su un file o quando l'utente fa clic sul comando **Cerca nei file** nella finestra di dialogo **trova e Sostituisci** . Per gestire queste situazioni, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> per gestire il processo di ricerca del progetto migliore per l'apertura di un documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Priorità progetto](../../extensibility/internals/project-priority.md)   
 [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
