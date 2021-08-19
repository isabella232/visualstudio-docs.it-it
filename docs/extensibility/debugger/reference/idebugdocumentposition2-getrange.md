---
description: Ottiene l'intervallo per la posizione del documento.
title: IDebugDocumentPosition2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 211003c3d54b7f37979240e400e373db2782ac2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119477"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Ottiene l'intervallo per la posizione del documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametri
`pBegPosition`\
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che viene compilata con la posizione iniziale. Impostare questo argomento su un valore Null se queste informazioni non sono necessarie.

`pEndPosition`\
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che viene compilata con la posizione finale. Impostare questo argomento su un valore Null se queste informazioni non sono necessarie.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'intervallo specificato in una posizione del documento per un punto di interruzione della posizione viene usato dal motore di debug (DE) per cercare in anticipo un'istruzione che contribuisce effettivamente al codice. Si consideri il codice di esempio seguente:

```
Line 5: // comment
Line 6: x = 1;
```

 La riga 5 non genera codice per il programma in fase di debug. Se il debugger che imposta il punto di interruzione alla riga 5 vuole che il de venga cercato in avanti per la prima riga che contribuisce al codice, il debugger specifica un intervallo che include righe candidate aggiuntive in cui un punto di interruzione potrebbe essere inserito correttamente. Il de cerca quindi in avanti attraverso tali righe finché non trova una riga che può accettare un punto di interruzione.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
