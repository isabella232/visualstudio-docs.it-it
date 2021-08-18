---
description: Restituisce un oggetto contesto del codice corrispondente a un identificatore di posizione del codice specificato.
title: IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ebecbc3ef26ae1f297d773bccafbe5f740d62a0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079298"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Restituisce un oggetto contesto del codice corrispondente a un identificatore di posizione del codice specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametri
`uCodeLocationId`\
[in] Specifica l'identificatore del percorso del codice. Per una descrizione di un identificatore della posizione del codice, vedere la sezione Osservazioni relativa al metodo [GetCodeLocationId.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

`ppCodeContext`\
[out] Restituisce un [oggetto IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta il contesto del codice associato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'identificatore della posizione del codice può essere restituito da una chiamata al [metodo GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) e può essere visualizzato nella [struttura DisassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

 Per convertire un contesto del codice in un identificatore di posizione del codice, chiamare il [metodo GetCodeLocationId.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

## <a name="see-also"></a>Vedi anche
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
