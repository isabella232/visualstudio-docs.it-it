---
description: Determina se la gestione del debug di sessione (SDM) può scollegare il processo.
title: IDebugProcess2::CanDetach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c891ac19158cb5f37f13dd0c93696a0cfe1671e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159855"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Determina se la gestione del debug di sessione (SDM) può scollegare il processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, `S_OK.` restituisce Restituisce se il debugger non è in grado di `S_FALSE` disconnettersi dal processo. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
