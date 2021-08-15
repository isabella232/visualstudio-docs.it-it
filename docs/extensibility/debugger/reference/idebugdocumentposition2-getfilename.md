---
description: Ottiene il nome del file di origine che contiene la posizione del documento.
title: IDebugDocumentPosition2::GetFileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46e57b8e836e3a1f3de7bf12f6bd35a8b27084a79afdfec45a7acd4a85ad1438
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262009"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Ottiene il nome del file di origine che contiene la posizione del documento.

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
[out] Restituisce il nome del file di origine.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un file di origine potrebbe non avere sempre un nome file( ad esempio, il file di origine potrebbe non esistere su disco).

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
