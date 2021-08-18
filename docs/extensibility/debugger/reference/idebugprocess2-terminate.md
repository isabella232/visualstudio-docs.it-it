---
description: Termina il processo.
title: IDebugProcess2::Terminate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Terminate
helpviewer_keywords:
- IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2903c56a89a1f4fed260fbdeb86859fbf1c3ee6c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072015"
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
Termina il processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Quando un processo viene terminato, tutti i programmi all'interno di tale processo vengono terminati; none è autorizzato a eseguire altro codice.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
