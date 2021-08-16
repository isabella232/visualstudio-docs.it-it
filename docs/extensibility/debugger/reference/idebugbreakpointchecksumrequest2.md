---
description: Rappresenta un checksum del documento per una richiesta di punto di interruzione.
title: Oggetto IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9562b5d89b0602140a84620b97e4ec43b9cab7b292c8698d229c8f5b604197a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378016"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Rappresenta un checksum del documento per una richiesta di punto di interruzione.

## <a name="syntax"></a>Sintassi

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dal pacchetto [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] di debug e utilizzato dai motori di debug.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono illustrati i metodi di `IDebugBreakpointChecksumRequest2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Recupera il checksum del documento per una richiesta di punto di interruzione in base all'identificatore univoco dell'algoritmo di checksum da utilizzare.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Determina se il checksum è abilitato per questo documento.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
