---
title: Gestione di annullamento e ripristino con l'API Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c43dc4892f1cf2a938a4ed29fc68bc55e99cc05e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948128"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gestire l'annullamento e ripristino con l'API legacy
Editor devono supportare operazioni di annullamento che consentono agli utenti di annullare le modifiche recenti quando si modificano codice. La maggior parte degli editor implementati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] può avere il supporto di annullamento fornito automaticamente dall'ambiente di sviluppo integrato (IDE).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Procedura: Gestione dell'annullamento implementare](../extensibility/how-to-implement-undo-management.md)  
 Fornisce funzionalità di annullamento per gli editor con uno o più visualizzazioni.  
  
 [Procedura: Cancella lo stack di annullamento](../extensibility/how-to-clear-the-undo-stack.md)  
 Viene descritto come cancellare un stack di annullamento.  
  
 [Procedura: Usare la gestione di annullamento collegato](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora l'editor di gestione di annullamento collegata.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornisce la gestione di annullamento per un editor che supporta più visualizzazioni.  
