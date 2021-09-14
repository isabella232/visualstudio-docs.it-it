---
description: Recupera l'intervallo per la posizione corrente del documento.
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a262287e6dc84316686f1132ed0ac496eee35e0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634963"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera l'intervallo per la posizione corrente del documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parametri
`pdwBegOffset`\
[in, out] Offset per la posizione iniziale dell'intervallo. Impostare questo parametro su un valore Null se queste informazioni non sono necessarie.

`pdwEndOffset`\
[in, out] Offset per la posizione finale dell'intervallo. Impostare questo parametro su un valore Null se queste informazioni non sono necessarie.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'intervallo specificato in una posizione del documento per un punto di interruzione della posizione viene usato dal motore di debug per cercare in anticipo un'istruzione che effettivamente contribuisce al codice. Si consideri il codice di esempio seguente:

```
Line 5: // comment
Line 6: x = 1;
```

 La riga 5 non genera codice per il programma di cui è in corso il debug. Se il debugger che imposta il punto di interruzione alla riga 5 vuole che DE eserviti la ricerca in avanti di una determinata quantità per la prima riga che contribuisce al codice, il debugger specifica un intervallo che include righe candidate aggiuntive in cui un punto di interruzione potrebbe essere posizionato correttamente. De cerca quindi in avanti nelle righe fino a quando non trova una riga che può accettare un punto di interruzione.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
