---
title: Proprietà IDebugEngine3 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730646"
---
# <a name="idebugengine3"></a>IDebugEngine3
Rappresenta un singolo motore di debug (DE) che controlla il debug di uno o più moduli.

## <a name="syntax"></a>Sintassi

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un DE personalizzato (se supporta i simboli) per abilitare lo stato JustMyCode.This interface is implemented by a custom DE (if it supports symbols) to enable the JustMyCode state. Questa interfaccia deve essere implementata dal DE se supporta i simboli e JustMyCode.This interface must be implemented by the DE if it supports symbols and JustMyCode.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata dal gestore di sessione di debug (SDM) per passare le opzioni utente per i percorsi da cui caricare i simboli. Viene anche chiamato per impostare il GUID del motore quando viene creata un'istanza (questo GUID si basa sulle metriche dal momento della registrazione del motore). Il file SDM chiama anche questa interfaccia per impostare lo stato JustMyCode e per impostare tutte le eccezioni note dal debugger a uno stato specificato.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), l'interfaccia `IDebugEngine3` espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Imposta il percorso o i percorsi che il DE utilizzerà per la ricerca di simboli di debug.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carica i simboli per tutti i moduli che non hanno ancora caricato i simboli.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indica al DE le informazioni JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Imposta il GUID DE dalle metriche.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Impostare tutte le eccezioni attualmente in sospeso su uno stato specificato.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
