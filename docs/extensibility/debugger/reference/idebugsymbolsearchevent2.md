---
description: Questa interfaccia viene inviata dal motore di debug per indicare che sono stati caricati i simboli di debug per un modulo in fase di debug.
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d61bcc7c77295b59bc6cc66cd1cf9aac3486e6c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103650"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Questa interfaccia viene inviata dal motore di debug per indicare che sono stati caricati i simboli di debug per un modulo in fase di debug.

## <a name="syntax"></a>Sintassi

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 De implementa questa interfaccia per segnalare che i simboli di un modulo sono stati caricati. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 De crea e invia questo oggetto evento per segnalare che i simboli di un modulo sono stati caricati. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 `IDebugSymbolSearchEvent2`L'interfaccia espone il metodo seguente.

|Metodo|Descrizione|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Recupera informazioni sui risultati di una ricerca di simboli.|

## <a name="remarks"></a>Commenti
 Questo evento verrà inviato anche se non è stato possibile caricare i simboli. La `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` chiamata di consente al gestore di questo evento di determinare se il modulo ha effettivamente simboli.

 Visual Studio usa in genere questo evento per aggiornare lo stato dei simboli caricati nella **finestra** Moduli.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
