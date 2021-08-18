---
description: Imposta la risposta, se presente, dalla finestra di messaggio.
title: IDebugMessageEvent2::SetResponse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d71b782bd8704ef221985cf10e8ffa38d350b7d2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088484"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
Imposta la risposta, se presente, dalla finestra di messaggio.

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
[in] Specifica la risposta, usando le convenzioni della funzione `MessageBox` Win32. Per informazioni [dettagliate, vedere la funzione AfxMessageBox.](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
