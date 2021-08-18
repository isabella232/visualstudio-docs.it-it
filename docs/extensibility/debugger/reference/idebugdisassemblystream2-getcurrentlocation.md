---
description: Restituisce un identificatore della posizione del codice che rappresenta la posizione del codice corrente.
title: IDebugDisassemblyStream2::GetCurrentLocation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82d7e4d6c4e86dcab4cf384c5c3f2a8b8f5a522f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119659"
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
Restituisce un identificatore della posizione del codice che rappresenta la posizione del codice corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCurrentLocation( 
   UINT64* puCodeLocationId
);
```

```csharp
int GetCurrentLocation( 
   out ulong puCodeLocationId
);
```

## <a name="parameters"></a>Parametri
`puCodeLocationId`\
[out] Restituisce l'identificatore della posizione del codice. Per una descrizione di un identificatore di posizione del codice, vedere la sezione Osservazioni per il metodo [GetCodeLocationId.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'identificatore della posizione del codice può essere convertito in un contesto di codice chiamando il [metodo GetCodeContext.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
