---
title: Gestione di annullamento e ripristino con l'API Legacy | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194362"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Gestione delle fasi di rollback e di rollforward tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor devono supportare operazioni di annullamento che consentono agli utenti di annullare le modifiche recenti quando si modificano codice. La maggior parte degli editor implementati in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] può avere il supporto di annullamento fornito automaticamente dall'ambiente di sviluppo integrato (IDE).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: implementare la gestione della fase di rollback](../extensibility/how-to-implement-undo-management.md)  
 Fornisce funzionalità di annullamento per gli editor con uno o più visualizzazioni.  
  
 [Procedura: cancellare lo stack della fase di rollback](../extensibility/how-to-clear-the-undo-stack.md)  
 Viene descritto come cancellare un stack di annullamento.  
  
 [Procedura: usare la gestione della fase di rollback collegata](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora l'editor di gestione di annullamento collegata.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornisce la gestione di annullamento per un editor che supporta più visualizzazioni.  
  
## <a name="related-sections"></a>Sezioni correlate
