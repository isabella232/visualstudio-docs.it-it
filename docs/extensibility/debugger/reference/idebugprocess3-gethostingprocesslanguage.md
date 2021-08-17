---
description: Questo metodo restituisce un GUID che rappresenta la lingua di questo processo come impostato da una chiamata a SetHostingProcessLanguage.
title: Interfaccia IDebugProcess3::GetHostingProcessLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d3ae1425e98fcc923c1be1d4d2af7e64837371f57e29934afb8ba08f592ce22
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416183"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
Questo metodo restituisce un oggetto che rappresenta la lingua di questo processo come impostato da `GUID` una chiamata a [SetHostingProcessLanguage.](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetHostingProcessLanguage(
   GUID* pguidLang
);
```

```csharp
int GetHostingProcessLanguage(
   out Guid pguidLang
);
```

## <a name="parameters"></a>Parametri
`pguidLang`\
[out] Oggetto `GUID` del linguaggio di questo processo. `GUID_NULL` (C++) o `Guid.Empty` (C#) indica che il linguaggio non è impostato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)
