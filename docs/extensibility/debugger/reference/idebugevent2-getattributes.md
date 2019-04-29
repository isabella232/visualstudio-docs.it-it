---
title: IDebugEvent2::GetAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 140b47af958e8f4623dd5921aa6046926737cf38
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920084"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Ottiene gli attributi per questo evento di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

#### <a name="parameters"></a>Parametri
 `pdwAttrib`

 [out] Una combinazione di flag dal [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia è comune a tutti gli eventi. Questo metodo viene descritto il tipo di evento. ad esempio, è l'evento sincrono o asincrono e si tratta di un evento di arresto.

## <a name="see-also"></a>Vedere anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)