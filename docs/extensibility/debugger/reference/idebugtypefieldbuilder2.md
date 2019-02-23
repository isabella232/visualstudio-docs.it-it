---
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97e0903d23b94019016634637cc18295efacd699
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688787"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Estende la **IDebugTypeFieldBuilder** sia in grado di creare tipi di matrice.

## <a name="syntax"></a>Sintassi

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia può essere ottenuta dal provider di simboli.

## <a name="methods"></a>Metodi
 Oltre ai metodi nel [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) interfaccia, questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crea una matrice del tipo specificato e delle dimensioni.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll