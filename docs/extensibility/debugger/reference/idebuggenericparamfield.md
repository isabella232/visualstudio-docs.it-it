---
title: Proprietà IDebugGenericParamField . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b04b0805aec5ecee818fa42e1d76a76cce12b66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727850"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Rappresenta un parametro per un tipo generico di codice gestito.

## <a name="syntax"></a>Sintassi

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Utilizzato per il supporto di generics.

## <a name="methods"></a>Metodi
 Oltre ai metodi sul IDebugField interfaccia, questa interfaccia implementa i metodi seguenti:In addition to the methods on the [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, this interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Restituisce il numero di vincoli associati a questo parametro generico.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Recupera i vincoli associati a questo parametro generico.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Recupera i flag per questo parametro generico.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Recupera l'indice di questo parametro generico.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Recupera il nome di questo parametro generico.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Recupera il proprietario del tipo o del metodo di questo parametro generico.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
