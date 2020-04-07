---
title: IDebugCoreServer3::EnableAutoAttach Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732920"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Abilita il collegamento automatico per i motori di debug specificati.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parametri
`rgguidSpecificEngines`\
[in] Matrice di GUID per ogni motore di debug da contrassegnare come collegamento automatico.

`celtSpecificEngines`\
[in] Il numero di motori `rgguidSpecificEngines`specificato in .

`pszStartPageUrl`\
[in] URL iniziale da utilizzare durante il collegamento automatico.

`pbstrSessionID`\
[fuori] ID della sessione collegata automaticamente.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce il codice di errore. Un codice `E_AUTO_ATTACH_NOT_REGISTERED`di errore è , che indica che la class factory di collegamento automatico non è stata registrata.

## <a name="remarks"></a>Osservazioni
 Quando viene avviato un programma associato all'URL specificato, i motori di debug specificati vengono avviati e collegati automaticamente.

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
