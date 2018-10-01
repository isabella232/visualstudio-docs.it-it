---
title: Gestione di annullamento e ripristino con l'API Legacy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bb1cc883941c8365e4d4341c93084beaef44d48
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529849"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>La gestione di annullamento e ripristino con l'API Legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [annullare la gestione e il ripristino usando l'API Legacy](https://docs.microsoft.com/visualstudio/extensibility/managing-undo-and-redo-by-using-the-legacy-api).  
  
Editor devono supportare operazioni di annullamento che consentono agli utenti di annullare le modifiche recenti quando si modificano codice. La maggior parte degli editor implementati in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] può avere il supporto di annullamento fornito automaticamente dall'ambiente di sviluppo integrato (IDE).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Implementare la gestione della fase di rollback](../extensibility/how-to-implement-undo-management.md)  
 Fornisce funzionalità di annullamento per gli editor con uno o più visualizzazioni.  
  
 [Procedura: Cancellare lo stack di fasi di rollback](../extensibility/how-to-clear-the-undo-stack.md)  
 Viene descritto come cancellare un stack di annullamento.  
  
 [Procedura: Usare la gestione della fase di rollback collegata](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora l'editor di gestione di annullamento collegata.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornisce la gestione di annullamento per un editor che supporta più visualizzazioni.  
  
## <a name="related-sections"></a>Sezioni correlate

