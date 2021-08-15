---
description: Ottiene l'ID processo della porta stessa.
title: IDebugPortEx2::GetPortProcessId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d90705ec4aee88e06209996fc47506ec23cf545e2132b37a245ef4bc111f0cd7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276945"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Ottiene l'ID processo della porta stessa.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>Parametri
`pdwProcessId`\
[out] Restituisce l'ID del processo fisico della porta stessa.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Nel runtime Win32, ad esempio, questo metodo chiama in genere la funzione Win32 `GetCurrentProcessId` per ottenere l'ID del processo fisico.

## <a name="see-also"></a>Vedi anche
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
