---
title: Proprietà IDebugCodeContext3 . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734182"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Estende il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaccia per consentire il recupero delle interfacce di modulo e di processo.

## <a name="syntax"></a>Sintassi

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dai motori di debug [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] e utilizzato dal pacchetto Debug.

## <a name="methods"></a>Metodi
 Oltre ai metodi `IDebugCodeContext2` sull'interfaccia, questa interfaccia implementa i metodi seguenti:In addition to the methods on the interface, this interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[Metodo GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera un riferimento all'interfaccia del modulo di debug.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera un riferimento all'interfaccia del processo di debug.|

## <a name="remarks"></a>Osservazioni
 Si tratta di un'interfaccia facoltativa che in genere non deve essere implementata.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
