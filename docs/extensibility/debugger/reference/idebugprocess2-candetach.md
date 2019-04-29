---
title: IDebugProcess2::CanDetach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad1a127a390b27a08a89ac939d9dcce60e60a64e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871070"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Determina se il gestore di debug di sessione (SDM) è possibile scollegare il processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK.` restituisce `S_FALSE` se il debugger non è possibile disconnettersi dal processo. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)