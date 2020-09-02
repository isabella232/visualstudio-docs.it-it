---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734182"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Estende l'interfaccia [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) per abilitare il recupero delle interfacce del modulo e del processo.

## <a name="syntax"></a>Sintassi

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dai motori di debug e utilizzato dal [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pacchetto di debug.

## <a name="methods"></a>Metodi
 Oltre ai metodi sull' `IDebugCodeContext2` interfaccia, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera un riferimento all'interfaccia del modulo di debug.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera un riferimento all'interfaccia del processo di debug.|

## <a name="remarks"></a>Osservazioni
 Si tratta di un'interfaccia facoltativa che in genere non è necessario implementare.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
