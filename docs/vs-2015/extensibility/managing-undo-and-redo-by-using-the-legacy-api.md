---
title: Gestione delle operazioni di annullamento e ripristino tramite l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194362"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Gestione delle fasi di rollback e di rollforward tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli editor devono supportare operazioni di annullamento che consentono agli utenti di annullare le modifiche recenti quando modificano il codice. La maggior parte degli editor implementati in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] può disporre del supporto di annullamento automaticamente fornito dal Integrated Development Environment (IDE).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Procedura: Implementare la gestione della fase di rollback](../extensibility/how-to-implement-undo-management.md)  
 Fornisce funzionalità di annullamento per gli editor con visualizzazioni singole o multiple.  
  
 [Procedura: Cancellare lo stack di fasi di rollback](../extensibility/how-to-clear-the-undo-stack.md)  
 Viene descritto come cancellare uno stack di annullamento.  
  
 [Procedura: Usare la gestione della fase di rollback collegata](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora la gestione degli annullamenti collegati nell'editor.  
  
## <a name="reference"></a>Riferimento  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornisce la gestione dell'annullamento per un editor che supporta più visualizzazioni.  
  
## <a name="related-sections"></a>Sezioni correlate
