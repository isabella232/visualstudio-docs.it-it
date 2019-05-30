---
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ee91686051440fe44efd1f4e4f9ba933f3e0c99
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323706"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Ottiene il modulo che viene caricato o scaricato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Parametri
`pModule`\
[out] Restituisce un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) oggetto che rappresenta il modulo che è il caricamento o scaricamento.

`pbstrDebugMessage`\
[in, out] Restituisce un messaggio facoltativo che descrive questo evento. Se questo parametro è un valore null, non viene richiesto alcun messaggio.

`pbLoad`\
[in, out] Diverso da zero (`TRUE`) se il modulo è il caricamento e zero (`FALSE`) se il modulo di scaricamento. Se questo parametro è un valore null, non è richiesto alcun lo stato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)