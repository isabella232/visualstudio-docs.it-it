---
title: Supporto della procedura guidata per i progetti annidati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3231dd48cea43f517a5e59f33c80df655032ec0c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990129"
---
# <a name="wizard-support-for-nested-projects"></a>Supporto di procedure guidate per i progetti annidati
L'IDE viene eseguito due procedure guidate che può implementare il progetto principale per i progetti annidati: il **nuovo progetto** procedura guidata e il **Aggiungi elemento** procedura guidata.  
  
 Se un utente avvia il **nuovo progetto** procedura guidata, selezionando **Aggiungi progetto** e facendo clic su **nuovo progetto** dal menu File o selezionando **Aggiungi** pulsante destro del mouse **nuovo progetto** in Esplora soluzioni nell'IDE vengono eseguiti il **AddProject** comando e l'implementazione del progetto padre del **AddProject**comando restituisce un file di progetto di modello o un file di procedura guidata (con estensione vsz) che include un set di parametri di contesto.  
  
 Analogamente, implementazione di un padre del progetto del **AddItem** procedure guidate restituisce un file con estensione vsz con un diverso set di parametri di contesto.  
  
 Per altre informazioni sulle procedure guidate, vedere [Wizard (. File vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [i parametri di contesto](../../extensibility/internals/context-parameters.md) e [registrazione Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)