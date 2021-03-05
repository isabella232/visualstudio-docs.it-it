---
description: Ottiene il nome file del file di origine che contiene la posizione del documento.
title: 'IDebugDocumentPosition2:: GetFileName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9bf6eb084c8122c940e49a006a09aa53e12cd8a8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162758"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Ottiene il nome file del file di origine che contiene la posizione del documento.

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
out Restituisce il nome del file di origine.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un file di origine potrebbe non avere sempre un nome file (ad esempio, il file di origine potrebbe non esistere sul disco).

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
