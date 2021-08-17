---
description: Verifica che un fornitore di porte possa aggiungere nuove porte.
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3203dd3ec8669a3adf37580398d1089d9a93776b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088185"
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
 Se la porta può essere aggiunta, restituisce . In caso contrario, restituisce per indicare che non è possibile `S_OK` aggiungere porte a questo fornitore di `S_FALSE` porte.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo prima di chiamare il [metodo AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) perché quest'ultimo metodo crea la porta e la aggiunge, operazione che potrebbe richiedere molto tempo.

## <a name="see-also"></a>Vedi anche
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
