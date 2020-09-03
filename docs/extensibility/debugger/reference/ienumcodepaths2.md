---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717722"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Questa interfaccia rappresenta un elenco di percorsi di codice.

## <a name="syntax"></a>Sintassi

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di percorsi di codice.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IEnumCodePaths2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera un numero specificato di percorsi di codice in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignora un numero specificato di percorsi di codice in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Ottiene il numero di percorsi di codice in un enumeratore.|

## <a name="remarks"></a>Osservazioni
 Un percorso di codice rappresenta un punto di ramo o una chiamata di funzione in un programma. Un elenco di percorsi di codice rappresenta il percorso in cui è stata eseguita l'esecuzione del codice.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
