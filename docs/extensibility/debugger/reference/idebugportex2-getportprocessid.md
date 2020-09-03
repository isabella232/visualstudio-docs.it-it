---
title: 'IDebugPortEx2:: GetPortProcessId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae974461e312c68e6fcc14150a08879ac7709950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725145"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Ottiene l'ID del processo della porta stessa.

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
out Restituisce l'ID del processo fisico della porta stessa.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Nel runtime Win32, ad esempio, questo metodo chiama in genere la funzione Win32 `GetCurrentProcessId` per ottenere l'ID del processo fisico.

## <a name="see-also"></a>Vedere anche
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
