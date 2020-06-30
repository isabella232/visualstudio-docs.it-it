---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: interface
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
ms.openlocfilehash: 1ec01ebc32472e315fe2c905ecfd2cfef0f4bbe1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541011"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Chiamato subito prima dello scaricamento di un componente aggiuntivo VSTO gestito.

## <a name="syntax"></a>Sintassi

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Osservazioni
 Questo metodo non viene chiamato da versioni correnti di Microsoft Office. Questo metodo è riservato per utilizzi futuri.

## <a name="see-also"></a>Vedere anche
- [Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
