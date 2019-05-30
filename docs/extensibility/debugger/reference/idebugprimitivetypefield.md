---
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4012b919cffc5e16433567fac283ac731d4d215c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353272"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Rappresenta un valore di enumerazione di tipo primitivo da un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Metodi
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia, questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Recupera il tipo primitivo associato a questo campo.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll