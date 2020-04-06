---
title: Proprietà IDebugModOpt . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726991"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Rappresenta un modificatore facoltativo di debug.

## <a name="syntax"></a>Sintassi

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Ottenuto da un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta una classe o un metodo.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa il metodo seguente:This interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera un elenco di modificatori facoltativi.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
