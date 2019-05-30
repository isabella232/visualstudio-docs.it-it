---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 165bbf6326bee67718c4c2ae44933d1b21b8252c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319785"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Rappresenta la possibilità di creare un campo che rappresenta un tipo.

## <a name="syntax"></a>Sintassi

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è ottenuta dal provider di simboli.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Crea un oggetto che rappresenta un tipo primitivo.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crea un puntatore al tipo specificato.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll