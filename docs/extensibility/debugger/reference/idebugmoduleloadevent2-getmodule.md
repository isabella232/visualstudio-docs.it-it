---
description: Ottiene il modulo che viene caricato o scaricato.
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c632f0de62f931b68b56c321e846eca9265f50b9c19f0704da7fee2b7bd8a8ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417041"
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
[out] Restituisce un [oggetto IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) che rappresenta il modulo che sta caricando o scaricando.

`pbstrDebugMessage`\
[in, out] Restituisce un messaggio facoltativo che descrive questo evento. Se questo parametro è un valore Null, non viene richiesto alcun messaggio.

`pbLoad`\
[in, out] Diverso da zero ( `TRUE` ) se il modulo viene caricato e zero ( ) se il modulo è in fase di `FALSE` scaricamento. Se questo parametro è un valore Null, non viene richiesto alcuno stato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
