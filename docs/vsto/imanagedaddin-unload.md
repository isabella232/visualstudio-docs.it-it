---
title: IManagedAddin::Unload
description: Chiamato subito prima dello scaricamento di un componente aggiuntivo VSTO gestito.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f877150a747984d0d04f779b16338d04fd55f1ba
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633844"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Chiamato subito prima dello scaricamento di un componente aggiuntivo VSTO gestito.

## <a name="syntax"></a>Sintassi

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Commenti
 Questo metodo non viene chiamato da versioni correnti di Microsoft Office. Questo metodo è riservato per utilizzi futuri.

## <a name="see-also"></a>Vedi anche
- [Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
