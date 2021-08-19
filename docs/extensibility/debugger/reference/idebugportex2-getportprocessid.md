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
ms.openlocfilehash: 696ba253090bdec5c31ed814e465b2a5afca87f2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088237"
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
