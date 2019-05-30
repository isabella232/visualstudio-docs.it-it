---
title: IDebugMessageEvent2::SetResponse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40d12bd15f496c41463aed231345a75a27301835
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346862"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
Imposta la risposta, se presente, nella finestra di messaggio.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetResponse( 
   DWORD dwResponse
);
```

```csharp
int SetResponse( 
   uint dwResponse
);
```

## <a name="parameters"></a>Parametri
`dwResponse`\
[in] Specifica la risposta, usando le convenzioni di Win32 `MessageBox` (funzione). Vedere le [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) funzione per i dettagli.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)