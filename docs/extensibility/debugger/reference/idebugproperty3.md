---
title: Proprietà IDebugProperty3 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2819724c204631112fd1a3e827126c4bc176972
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721049"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Questa interfaccia fornisce il supporto per:This interface provides support for:

- Recupero di una stringa arbitrariamente lunga associata alla proprietà.

- Associazione di un ID univoco alla proprietà.

- Recupero di un elenco di visualizzatori personalizzati per la proprietà.

- Impostazione del valore di una proprietà con la possibilità di segnalare eventuali errori risultanti

## <a name="syntax"></a>Sintassi

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia sullo stesso oggetto che implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) per fornire il supporto per lunghe stringhe, ID di proprietà e visualizzatori personalizzati.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) `IDebugProperty2` su un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati `IDebugProperty2` `IDebugProperty3` da , l'interfaccia espone i metodi riportati di seguito.

|Metodo|Descrizione|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Restituisce la lunghezza della stringa associata alla proprietà.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Restituisce la stringa in un buffer fornito dall'utente.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Crea un ID univoco per questa proprietà.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Elimina l'ID univoco per questa proprietà.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Restituisce il numero di visualizzatori personalizzati con cui questa proprietà può essere visualizzata.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Restituisce l'elenco di visualizzatori personalizzati con cui questa proprietà può essere visualizzata.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Imposta il valore di questa proprietà, restituendo un messaggio di errore in caso di problemi.|

## <a name="remarks"></a>Osservazioni
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) è il modo preferito per il gestore di sessione di debug (SDM) per impostare il valore di una proprietà.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
