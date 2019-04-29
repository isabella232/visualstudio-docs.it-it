---
title: Nascondere le proprietà con proprietà figlio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822386"
---
# <a name="hiding-properties-that-have-child-properties"></a>Nascondere le proprietà con proprietà figlio
Si desidera nascondere le proprietà con proprietà figlio:  
  
- Se si hanno progetti annidati in cui il progetto principale a livello di codice consente di controllare alcuni aspetti del progetto figlio.  
  
- Se si utilizza un controllo con una finestra di progettazione specializzata e non si desidera offrire agli sviluppatori l'accesso completo a tutte le proprietà del controllo.  
  
- Se si dispone della proprietà di ambito di un oggetto e si vuole limitare la visualizzazione delle proprietà.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Per nascondere le proprietà con proprietà figlio  
  
1. Impostare il `pfDisplay` nel parametro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> a `FALSE`.  
  
2. Impostare il `pfHide` nel parametro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> a `TRUE`.  
  
## <a name="see-also"></a>Vedere anche  
 [Griglia di visualizzazione delle proprietà](../extensibility/internals/properties-display-grid.md)