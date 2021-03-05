---
description: Rappresenta un campo dinamico per un oggetto IDebugBinder.
title: IDebugDynamicFieldCOMPlus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27fc3fb25b738db20d480a7a4542884dcb76123a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154030"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Rappresenta un campo dinamico per un oggetto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

## <a name="syntax"></a>Sintassi

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>Metodi
 Oltre ai metodi sull'interfaccia [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) , questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Recupera un tipo dato il tipo primitivo.|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Recupera un tipo in base al relativo token.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
