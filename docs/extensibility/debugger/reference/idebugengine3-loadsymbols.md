---
title: IDebugEngine3::LoadSymbols Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7963d39601a0d3a90ca2daa7632902d7aa506de8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730807"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Carica (se necessario) i simboli per tutti i moduli sottoposti a debug da questo motore di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario restituisce il codice di errore.

## <a name="remarks"></a>Osservazioni
 Vengono caricati i simboli di debug per tutti i moduli a cui fa riferimento questo motore di debug. I simboli vengono caricati solo se non sono già stati caricati. La ricerca di simboli viene eseguita nei percorsi impostati da una chiamata a [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Vedere anche
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
