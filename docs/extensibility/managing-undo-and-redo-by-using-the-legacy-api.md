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
ms.openlocfilehash: adf6a2405ae3d3408f9cf04199ba05dff9232326
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856434"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gestire l'annullamento e ripristino con l'API legacy
Editor devono supportare operazioni di annullamento che consentono agli utenti di annullare le modifiche recenti quando si modificano codice. La maggior parte degli editor implementati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] può avere il supporto di annullamento fornito automaticamente dall'ambiente di sviluppo integrato (IDE).

## <a name="in-this-section"></a>Contenuto della sezione
- [Procedura: Implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md) fornisce funzionalità di annullamento per gli editor con uno o più visualizzazioni.

- [Procedura: Cancella lo stack di annullamento](../extensibility/how-to-clear-the-undo-stack.md) viene descritto come cancellare un stack di annullamento.

- [Procedura: Usare la gestione di annullamento collegata](../extensibility/how-to-use-linked-undo-management.md) incorpora collegato nell'editor di gestione dell'annullamento.

## <a name="reference"></a>Riferimenti
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Fornisce la gestione di annullamento per un editor che supporta più visualizzazioni.
