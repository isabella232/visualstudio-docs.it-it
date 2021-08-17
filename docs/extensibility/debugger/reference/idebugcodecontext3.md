---
description: Estende l'interfaccia IDebugCodeContext2 per consentire il recupero delle interfacce del modulo e del processo.
title: Interfaccia IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 502867256f90574c2a75791b447b76b56af3a638
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079779"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Estende [l'interfaccia IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) per consentire il recupero delle interfacce del modulo e del processo.

## <a name="syntax"></a>Sintassi

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dai motori di debug e utilizzato dal pacchetto [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] di debug.

## <a name="methods"></a>Metodi
 Oltre ai metodi sull'interfaccia `IDebugCodeContext2` , questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera un riferimento all'interfaccia del modulo di debug.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera un riferimento all'interfaccia del processo di debug.|

## <a name="remarks"></a>Commenti
 Si tratta di un'interfaccia facoltativa che in genere non deve essere implementata.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
