---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b00ead2236a36c2fa12e1ad154b9f853aa2224d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732594"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Ottiene un enumeratore per tutti gli attributi personalizzati associati a questo campo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[fuori] Restituisce un [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) oggetto che rappresenta l'elenco di attributi personalizzati; in caso contrario, restituisce un valore null se non sono presenti attributi personalizzati.

## <a name="return-value"></a>Valore restituito
 Se S_OK, restituisce S_OK o S_FALSE se non sono presenti attributi personalizzati in questo campo. In caso contrario, restituisce un codice di errore;

## <a name="remarks"></a>Osservazioni
 Un campo può avere più attributi personalizzati.

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
