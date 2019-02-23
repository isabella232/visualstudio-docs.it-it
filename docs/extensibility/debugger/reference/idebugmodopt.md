---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1bbfbc6b6e567e0e56aa369f9c0d1f13a4cbe34
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690929"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Rappresenta un modificatore facoltativo di debug.

## <a name="syntax"></a>Sintassi

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Ottenuto da un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta una classe o metodo.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera un elenco di modificatori facoltativi.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll