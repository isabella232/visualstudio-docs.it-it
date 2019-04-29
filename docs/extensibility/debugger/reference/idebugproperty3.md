---
title: IDebugProperty3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e73310d8a1cff3b640896d9bb5883cf2508bda6e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869321"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Questa interfaccia fornisce supporto per:

- Recupero di una stringa di lunghezza arbitraria associata alla proprietà.

- Associare un ID univoco della proprietà.

- Recuperare un elenco di visualizzatori personalizzati per la proprietà.

- Impostazione del valore di una proprietà con la possibilità di segnalare eventuali errori risultanti

## <a name="syntax"></a>Sintassi

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia nello stesso oggetto che implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) per fornire supporto per le stringhe lunghe, ID di proprietà e visualizzatori personalizzati.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProperty2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da `IDebugProperty2`, il `IDebugProperty3` interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Restituisce la lunghezza della stringa associata alla proprietà.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Restituisce la stringa in un buffer fornito dall'utente.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Crea un ID univoco per questa proprietà.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Elimina l'ID univoco per questa proprietà.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Restituisce il numero di visualizzatori personalizzati che può essere visualizzata con questa proprietà.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Restituisce l'elenco di visualizzatori personalizzati che può essere visualizzata con questa proprietà.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Imposta il valore di questa proprietà, restituendo un messaggio di errore se qualsiasi elemento è verificato un errore.|

## <a name="remarks"></a>Note
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) è il modo migliore per la gestione di debug (SDM) per impostare un valore della proprietà di sessione.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)