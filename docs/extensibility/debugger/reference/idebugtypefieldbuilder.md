---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81532e2616eefb9cb584eae1a70371fd2f963be1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718391"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Rappresenta la possibilità di creare un campo che rappresenta un tipo.

## <a name="syntax"></a>Sintassi

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene ottenuta dal provider di simboli.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Crea un oggetto che rappresenta un tipo primitivo.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crea un puntatore al tipo specificato.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
