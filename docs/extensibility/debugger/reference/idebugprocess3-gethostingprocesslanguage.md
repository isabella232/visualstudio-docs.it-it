---
title: 'IDebugProcess3:: GetHostingProcessLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b27be0850755a1a2808c8c5c758a3ad59b41d7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723625"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
Questo metodo restituisce un oggetto `GUID` che rappresenta la lingua del processo impostata da una chiamata a [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetHostingProcessLanguage(
   GUID* pguidLang
);
```

```csharp
int GetHostingProcessLanguage(
   out Guid pguidLang
);
```

## <a name="parameters"></a>Parametri
`pguidLang`\
out Oggetto `GUID` della lingua del processo. `GUID_NULL` (C++) o `Guid.Empty` (C#) indica che il linguaggio non è impostato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)
