---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 020062e97988fec4264e28526e512db3096e84c2
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200614"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Costruisce un'istanza del campo Data una matrice di argomenti di tipo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Parametri
`cArgs`\
[in] Numero di argomenti in di `ppArgs` matrice.

`ppArgs`\
[in] Matrice che contiene gli argomenti di tipo. Gli argomenti di tipo devono essere tipi chiusi (non generico o istanziato completa di generics).

`ppConstructedField`\
[out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia che rappresenta il nuovo campo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 I vincoli non vengono controllati.

## <a name="see-also"></a>Vedere anche
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)