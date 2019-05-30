---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37f4fd246c376d08ab3ca006c543b44c4db2d73d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340285"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Verifica che un fornitore di porte può aggiungere nuove porte.

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
 Se è possibile aggiungere la porta, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` per indicare Nessuna porta può essere aggiunto a questo fornitore della porta.

## <a name="remarks"></a>Note
 Chiamare questo metodo prima di chiamare il [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) metodo poiché quest'ultimo metodo consente di creare la porta, nonché aggiunta, che può essere un'operazione impegnativa.

## <a name="see-also"></a>Vedere anche
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)