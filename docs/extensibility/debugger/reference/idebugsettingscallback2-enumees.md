---
description: Enumera gli analizzatori di espressioni disponibili in base agli identificatori di lingua e fornitore.
title: 'IDebugSettingsCallback2:: enums | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7606bd46587c7141bddea0c822f08459f2d262d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075666"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Enumera gli analizzatori di espressioni disponibili in base agli identificatori di lingua e fornitore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Parametri
`celtBuffer`\
in Numero di elementi nel `pceltEEs` buffer.

`rgguidLang`\
[in, out] Identificatore univoco per il linguaggio di programmazione.

`rgguidVendor`\
[in, out] Identificatore univoco per il fornitore.

`pceltEEs`\
[in, out] Matrice di analizzatori di espressioni.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
