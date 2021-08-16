---
description: Questo metodo imposta il GUID del motore di debug (DE).
title: IDebugEngine3::SetEngineGuid | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca8010c09a703ed42b84a6585800d899ad5abb64f4cabf2cfced1ce38eb01d1e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390060"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
Questo metodo imposta l'oggetto del motore di debug `GUID` .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetEngineGuid(
   GUID* guidEngine
);
```

```csharp
int SetEngineGuid(
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Parametri
`guidEngine`\
[in] `GUID` del motore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
