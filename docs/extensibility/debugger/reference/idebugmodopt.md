---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e142ed1229f59cfc22ff33cba48e9e35eb4e4406
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726991"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Rappresenta un modificatore facoltativo di debug.

## <a name="syntax"></a>Sintassi

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Ottenuta da un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta una classe o un metodo.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera un elenco di modificatori facoltativi.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
