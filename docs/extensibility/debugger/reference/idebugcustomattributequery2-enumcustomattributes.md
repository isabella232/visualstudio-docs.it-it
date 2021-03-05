---
description: Ottiene un enumeratore per tutti gli attributi personalizzati collegati a questo campo.
title: 'IDebugCustomAttributeQuery2:: EnumCustomAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 348d5e753702e523f09bef8cbd5f374294c197e4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154444"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Ottiene un enumeratore per tutti gli attributi personalizzati collegati a questo campo.

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
out Restituisce un oggetto [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) che rappresenta l'elenco di attributi personalizzati. in caso contrario, restituisce un valore null se non sono presenti attributi personalizzati.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o S_FALSE se non sono presenti attributi personalizzati in questo campo. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Un campo può avere più attributi personalizzati.

## <a name="see-also"></a>Vedi anche
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
