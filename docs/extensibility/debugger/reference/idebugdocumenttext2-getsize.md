---
title: Proprietà IDebugDocumentText2::GetSize . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731584"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Recupera le dimensioni del testo in questa posizione nel documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Parametri
`pcNumLines`\
[fuori] Restituisce il numero di righe di testo.

`pcNumChars`\
[fuori] Restituisce il numero di caratteri del testo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni

 [Solo C) Se un particolare valore non è desiderato, passare un valore NULL per il parametro.

 [Solo In Cè] È necessario specificare entrambi i parametri.

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
