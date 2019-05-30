---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db3b27e510ccdbb5ec55c5bfae373114df0c9b16
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338981"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Estende la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaccia per abilitare il recupero delle interfacce di modulo e processo.

## <a name="syntax"></a>Sintassi

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementata dai motori di debug e utilizzato dal [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pacchetto di Debug.

## <a name="methods"></a>Metodi
 Oltre ai metodi nel `IDebugCodeContext2` interfaccia, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera un riferimento all'interfaccia del modulo di debug.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera un riferimento all'interfaccia del processo di debug.|

## <a name="remarks"></a>Note
 Si tratta di un'interfaccia opzionale che in genere non deve essere implementato.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll