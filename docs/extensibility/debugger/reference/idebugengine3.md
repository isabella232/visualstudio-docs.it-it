---
title: IDebugEngine3 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730646"
---
# <a name="idebugengine3"></a>IDebugEngine3
Rappresenta un motore di debug singolo (DE) che controlla il debug di uno o più moduli.

## <a name="syntax"></a>Sintassi

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un oggetto DE personalizzato (se supporta i simboli) per abilitare lo stato JustMyCode. Questa interfaccia deve essere implementata da DE se supporta i simboli e JustMyCode.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata da gestione debug sessione (SDM) per passare le opzioni utente per i percorsi da cui caricare i simboli. Viene anche chiamato per impostare il GUID del motore quando ne viene creata un'istanza (questo GUID è basato sulle metriche del momento della registrazione del motore). SDM chiama anche questa interfaccia per impostare lo stato JustMyCode e per impostare tutte le eccezioni note dal debugger su uno stato specificato.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), l' `IDebugEngine3` interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Imposta il percorso o i percorsi che il DE utilizzerà per cercare i simboli di debug.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carica i simboli per tutti i moduli per i quali non sono ancora stati caricati i simboli.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indica al DE le informazioni JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Imposta il GUID DE dalla metrica.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Imposta tutte le eccezioni attualmente in attesa su uno stato specificato.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
