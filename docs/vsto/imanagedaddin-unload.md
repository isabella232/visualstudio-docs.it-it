---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 68ef36185c193263db386a1e1f80877c0327440c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874341"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Chiamato subito prima dello scaricamento di un componente aggiuntivo VSTO gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```csharp
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## <a name="remarks"></a>Note  
 Questo metodo non viene chiamato da versioni correnti di Microsoft Office. Questo metodo è riservato per utilizzi futuri.  
  
## <a name="see-also"></a>Vedere anche  
 [IManagedAddin (interfaccia)](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
