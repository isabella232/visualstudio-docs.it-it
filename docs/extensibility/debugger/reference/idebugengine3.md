---
description: Rappresenta un singolo motore di debug che controlla il debug di uno o più moduli.
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f997a177164c66ac116db407db6e3edfcc571b0a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710301"
---
# <a name="idebugengine3"></a>IDebugEngine3
Rappresenta un singolo motore di debug che controlla il debug di uno o più moduli.

## <a name="syntax"></a>Sintassi

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un DE personalizzato (se supporta i simboli) per abilitare lo stato JustMyCode. Questa interfaccia deve essere implementata da DE se supporta i simboli e JustMyCode.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata da Gestione debug sessione (SDM) per passare le opzioni utente per i percorsi da cui caricare i simboli. Viene chiamato anche per impostare il GUID del motore quando viene creata un'istanza di tale GUID (questo GUID è basato sulle metriche dal momento della registrazione del motore). SDM chiama anche questa interfaccia per impostare lo stato JustMyCode e per impostare tutte le eccezioni note dal debugger su uno stato specificato.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) `IDebugEngine3` l'interfaccia espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Imposta il percorso o i percorsi che verranno utilizzati da DE per cercare i simboli di debug.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carica i simboli per tutti i moduli in cui non sono ancora stati caricati i simboli.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indica a DE le informazioni di JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Imposta il GUID DE dalle metriche.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Imposta tutte le eccezioni attualmente in sospeso su uno stato specificato.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
