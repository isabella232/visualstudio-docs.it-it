---
description: Recupera le dimensioni del testo in questa posizione nel documento.
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25fa2f9c4a36e292bf58c80cbfdb01c6ad021ce4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111254"
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
[out] Restituisce il numero di righe di testo.

`pcNumChars`\
[out] Restituisce il numero di caratteri di testo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti

 [Solo C++] Se non si desidera un valore specifico, passare un valore NULL per il parametro .

 [Solo C#] Entrambi i parametri devono essere specificati.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
