---
description: Rappresenta un checksum del documento per una richiesta del punto di interruzione.
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 78361429e371bf19ee1fea27c090af80c2b79b73
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078084"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Rappresenta un checksum del documento per una richiesta del punto di interruzione.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dal [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pacchetto di debug e utilizzato dai motori di debug.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugBreakpointChecksumRequest2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Recupera il checksum del documento per una richiesta del punto di interruzione in base all'identificatore univoco dell'algoritmo di checksum da utilizzare.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Determina se il checksum è abilitato per questo documento.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
