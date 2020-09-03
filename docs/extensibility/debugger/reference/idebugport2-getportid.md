---
title: 'IDebugPort2:: GetPortId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortId
helpviewer_keywords:
- IDebugPort2::GetPortId
ms.assetid: 837cb924-c113-4224-aa86-3e02b33dfa70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 97b0134b083b3f9b4697ce26bc4bd57c0b455a63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725412"
---
# <a name="idebugport2getportid"></a>IDebugPort2::GetPortId
Ottiene l'identificatore di porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPortId( 
   GUID* pguidPort
);
```

```csharp
int GetPortId( 
   out Guid pguidPort
);
```

## <a name="parameters"></a>Parametri
`pguidPort`\
out Restituisce il GUID che identifica la porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
