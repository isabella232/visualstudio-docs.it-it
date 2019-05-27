---
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d6f6672349d6a37d0f7b5e43c9a68d765d3abc7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202991"
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