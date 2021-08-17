---
description: Enumera gli attributi personalizzati.
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a3faf096d1cfee1bb2832ae6e0aae35eda135f0d9949c0f1b2eec9bbf49e6e03
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389228"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Enumera gli attributi personalizzati.

## <a name="syntax"></a>Sintassi

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia per supportare attributi personalizzati (tramite [l'interfaccia IDebugCustomAttribute).](../../../extensibility/debugger/reference/idebugcustomattribute.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
- [EnumCustomAttributes restituisce](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugCustomAttributes` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Recupera un numero specificato di attributi personalizzati in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Ignora un numero specificato di attributi personalizzati in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Ottiene il numero di attributi personalizzati in un enumeratore.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
