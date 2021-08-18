---
description: Costruisce un'istanza del campo in base a una matrice di argomenti di tipo.
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6047737d7b4aeee9d1ec74e4fe1fea57b1722ec
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096154"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Costruisce un'istanza del campo in base a una matrice di argomenti di tipo.

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
[in] Numero di argomenti nella `ppArgs` matrice.

`ppArgs`\
[in] Matrice contenente gli argomenti di tipo. Gli argomenti di tipo devono essere tipi chiusi (generics non generici o di cui è stata creata un'istanza completa).

`ppConstructedField`\
[out] Restituisce [l'interfaccia IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il nuovo campo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 I vincoli non vengono controllati.

## <a name="see-also"></a>Vedi anche
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
