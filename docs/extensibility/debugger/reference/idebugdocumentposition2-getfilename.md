---
title: IDebugDocumentPosition2::GetFileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 478f259d111e19df988c76733d1bb52655adab2c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326534"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Ottiene il nome del file del file di origine che contiene la posizione del documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetFileName( 
   BSTR* pbstrFileName
);
```

```csharp
int GetFileName( 
   out string pbstrFileName
);
```

## <a name="parameters"></a>Parametri
`pbstrFileName`\
[out] Restituisce il nome del file del file di origine.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Un file di origine non può sempre essere un nome di file (il file di origine potrebbe non esiste sul disco, ad esempio).

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)