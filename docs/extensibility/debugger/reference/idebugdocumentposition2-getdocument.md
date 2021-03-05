---
description: Ottiene il documento contenitore.
title: 'IDebugDocumentPosition2:: GetDocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetDocument
helpviewer_keywords:
- IDebugDocumentPosition2::GetDocument
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0153b55397b78191d1e2ddc022767095bc1fcd8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162797"
---
# <a name="idebugdocumentposition2getdocument"></a>IDebugDocumentPosition2::GetDocument
Ottiene il documento contenitore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDocument( 
   IDebugDocument2** ppDoc
);
```

```csharp
int GetDocument( 
   out IDebugDocument2 ppDoc
);
```

## <a name="parameters"></a>Parametri
`ppDoc`\
out Restituisce un oggetto [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) che rappresenta il documento contenente questa posizione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
