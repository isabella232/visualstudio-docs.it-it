---
title: IDebugDocumentPositionOffset2::GetRange . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731621"
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
[in, out] Offset per la posizione iniziale dell'intervallo. Impostare questo parametro su un valore null se queste informazioni non sono necessarie.

`pdwEndOffset`\
[in, out] Offset per la posizione finale dell'intervallo. Impostare questo parametro su un valore null se queste informazioni non sono necessarie.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 L'intervallo specificato in una posizione di documento per un punto di interruzione di posizione viene utilizzato dal motore di debug (DE) per cercare in anticipo un'istruzione che contribuisce effettivamente al codice. Si consideri il codice di esempio seguente:

```
Line 5: // comment
Line 6: x = 1;
```

 Riga 5 non fornisce codice al programma in fase di debug. Se il debugger che imposta il punto di interruzione nella riga 5 desidera che il DE per cercare in avanti una certa quantità per la prima riga che contribuisce al codice, il debugger specifica un intervallo che include ulteriori righe candidate in cui un punto di interruzione potrebbe essere posizionato correttamente. Il DE sarebbe quindi cercare in avanti attraverso tali righe fino a trovare una riga che potrebbe accettare un punto di interruzione.

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
