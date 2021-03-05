---
description: Imposta le impostazioni locali del motore di debug (DE).
title: 'IDebugEngine2:: setlocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54cfd2d9d51cbad414cfb481b88f1e3277500efa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153911"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Imposta le impostazioni locali del motore di debug (DE).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>Parametri
`wLangID`\
in Specifica le impostazioni locali della lingua. Ad esempio 1033 per l'inglese.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato da gestione debug sessione (SDM) per propagare le impostazioni locali dell'IDE in modo che le stringhe restituite da DE siano localizzate correttamente.

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
