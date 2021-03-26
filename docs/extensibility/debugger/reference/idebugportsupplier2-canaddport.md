---
description: Verifica che un fornitore di porte possa aggiungere nuove porte.
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad704eda53807d344b23736d2d9b55e172c36468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072208"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Verifica che un fornitore di porte possa aggiungere nuove porte.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Valore restituito
 Se è possibile aggiungere la porta, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` per indicare che non è possibile aggiungere porte al fornitore della porta.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo prima di chiamare il metodo [addport](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) poiché quest'ultimo crea la porta e la aggiunge, operazione che può richiedere molto tempo.

## <a name="see-also"></a>Vedi anche
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
