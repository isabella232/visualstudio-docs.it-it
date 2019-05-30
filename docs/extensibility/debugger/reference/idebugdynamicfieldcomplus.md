---
title: IDebugDynamicFieldCOMPlus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 824498f3d7657bcc5984d31a1abaa4e97c4a9a7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330195"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Rappresenta un campo dinamico per un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) oggetto.

## <a name="syntax"></a>Sintassi

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>Metodi
 Oltre ai metodi nel [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) interfaccia, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Recupera un tipo di dato il tipo primitivo.|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Recupera un tipo dato il relativo token.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll