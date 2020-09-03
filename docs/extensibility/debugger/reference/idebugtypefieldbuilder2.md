---
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed34284e373a7d96761aabe5a7f179367649bc0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718297"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Estende **IDebugTypeFieldBuilder** per poter creare tipi di matrici.

## <a name="syntax"></a>Sintassi

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia può essere ottenuta dal provider di simboli.

## <a name="methods"></a>Metodi
 Oltre ai metodi sull'interfaccia [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) , questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crea una matrice del tipo e delle dimensioni specificati.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
