---
description: Estende i tipi di campi disponibili per supportare i generics di codice gestito.
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8214703fb1ffc05d3f58f8348870a8505cc8f59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077187"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Estende i tipi di campi disponibili per supportare i generics di codice gestito.

## <a name="syntax"></a>Sintassi

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Metodi
 Oltre ai metodi sull'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Recupera il tipo di campo esteso specificato.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Determina se il campo rappresenta un tipo chiuso.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
