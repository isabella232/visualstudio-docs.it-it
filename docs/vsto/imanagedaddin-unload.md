---
title: IManagedAddin::Unload
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 283fd069e0de72af92f7999871190c6c8a0d345b
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Chiamato subito prima dello scaricamento di un componente aggiuntivo VSTO gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```c++
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## <a name="remarks"></a>Note  
 Questo metodo non viene chiamato da versioni correnti di Microsoft Office. Questo metodo è riservato per utilizzi futuri.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  