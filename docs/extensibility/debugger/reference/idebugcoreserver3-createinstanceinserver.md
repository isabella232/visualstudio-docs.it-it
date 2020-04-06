---
title: Proprietà IDebugCoreServer3::CreateInstanceInServer . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733012"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crea un'istanza di un motore di debug nel server.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametri
`szDll`\
[in] Percorso della dll che implementa il CLSID specificato nel `clsidObject` parametro. Se si `NULL`tratta di `CoCreateInstance` , viene chiamata la funzione di COM.

`wLangId`\
[in] Impostazioni locali del motore di debug. Può essere 0 se il [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) metodo non deve essere chiamato.

`clsidObject`\
[in] CLSID del motore di debug da creare.

`riid`\
[in] ID di interfaccia dell'interfaccia specifica da recuperare dall'oggetto classe.

`ppvObject`\
[fuori] `IUnknown` dall'oggetto di cui è stata creata un'istanza. Eseguire il cast o il marshalling di questo oggetto nell'interfaccia desiderata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
