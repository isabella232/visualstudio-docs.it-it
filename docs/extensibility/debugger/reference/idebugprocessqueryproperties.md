---
description: Questa interfaccia è un'interfaccia di estensione implementata dagli implementatori di IDebugProcess2.
title: Proprietà IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dad8262b2c8add1787d07dbd4589c2398d9c807abef5aaa06fc3ba46244f193
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433411"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Questa interfaccia è un'interfaccia di estensione implementata dagli [implementatori di IDebugProcess2.](../../../extensibility/debugger/reference/idebugprocess2.md) Consente all'implementatore di ottenere informazioni sull'ambiente del processo di debug.

## <a name="syntax"></a>Sintassi

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementare questa interfaccia per ottenere informazioni sull'ambiente di esecuzione di un processo di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProcessQueryProperties` .

|Metodo|Descrizione|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Esegue una query per il valore di una proprietà.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Esegue una query per i valori delle proprietà.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene implementata raramente.

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
