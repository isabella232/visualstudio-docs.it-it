---
description: Crea un'istanza di un motore di debug nel server.
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28aaadb7bd4e319a47d77f9577e7e58206b72d46
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079571"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crea un'istanza di un motore di debug nel server.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
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
[in] Percorso della DLL che implementa il CLSID specificato nel `clsidObject` parametro . Se è `NULL` , viene chiamata la funzione di `CoCreateInstance` COM.

`wLangId`\
[in] Impostazioni locali del motore di debug. Può essere 0 se il [metodo SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) non deve essere chiamato.

`clsidObject`\
[in] CLSID del motore di debug da creare.

`riid`\
[in] ID di interfaccia dell'interfaccia specifica da recuperare dall'oggetto classe.

`ppvObject`\
[out] `IUnknown` Interfaccia dall'oggetto di cui è stata creata un'istanza. Eseguire il cast o il marshalling di questo oggetto nell'interfaccia desiderata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
