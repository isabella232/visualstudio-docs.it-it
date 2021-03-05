---
description: Abilita il fissaggio automatico per i motori di debug specificati.
title: 'IDebugCoreServer3:: EnableAutoAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 644d238db11c117b9068de8f7903361b9712f3aa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163148"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Abilita il fissaggio automatico per i motori di debug specificati.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parametri
`rgguidSpecificEngines`\
in Matrice di GUID per ogni motore di debug da contrassegnare come connessione automatica.

`celtSpecificEngines`\
in Numero di motori specificati in `rgguidSpecificEngines` .

`pszStartPageUrl`\
in URL iniziale da utilizzare per il fissaggio automatico.

`pbstrSessionID`\
out ID della sessione collegata automaticamente.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice errore. Un codice di errore è `E_AUTO_ATTACH_NOT_REGISTERED` , che indica che il class factory di connessione automatica non è stato registrato.

## <a name="remarks"></a>Commenti
 Quando viene avviato un programma associato all'URL specificato, i motori di debug specificati vengono avviati automaticamente e collegati.

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
