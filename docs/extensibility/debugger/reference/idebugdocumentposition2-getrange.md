---
title: 'IDebugDocumentPosition2:: GetRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731671"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Ottiene l'intervallo per questa posizione del documento.

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
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) compilata con la posizione iniziale. Se queste informazioni non sono necessarie, impostare questo argomento su un valore null.

`pEndPosition`\
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) compilata con la posizione finale. Se queste informazioni non sono necessarie, impostare questo argomento su un valore null.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 L'intervallo specificato in una posizione del documento per un punto di interruzione del percorso viene utilizzato dal motore di debug (DE) per eseguire una ricerca in avanti di un'istruzione che contribuisce effettivamente al codice. Si consideri il codice di esempio seguente:

```
Line 5: // comment
Line 6: x = 1;
```

 La riga 5 non contribuisce al programma di cui è in corso il debug. Se il debugger che imposta il punto di interruzione nella riga 5 vuole che il DE cerchi in avanti una determinata quantità per la prima riga che contribuisce al codice, il debugger specifica un intervallo che include righe candidati aggiuntive in cui un punto di interruzione può essere inserito correttamente. Il DE, quindi, ricercherà le righe fino a trovare una riga che potrebbe accettare un punto di interruzione.

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
