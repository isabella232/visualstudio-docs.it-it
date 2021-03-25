---
description: Il motore di debug (DE) usa questa interfaccia per richiedere il caricamento di un documento.
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbf24620b3dfa508a52463598219be4b2d7439a8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094401"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Il motore di debug (DE) usa questa interfaccia per richiedere il caricamento di un documento.

## <a name="syntax"></a>Sintassi

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia quando è necessario che venga aperto un file di origine. Questa interfaccia viene implementata solo dai motori di debug che funzionano con o fanno parte di interpreti di script. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (il SDM USA [QueryInterface](/cpp/atl/queryinterface) per accedere all' `IDebugEvent2` interfaccia).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento quando è necessario aprire un file di origine. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugActivateDocumentEvent2` .

|Metodi|Descrizione|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Ottiene il documento da attivare.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Ottiene il contesto del documento che descrive la posizione all'interno del documento.|

## <a name="remarks"></a>Commenti
 Uno scenario tipico in cui viene utilizzata questa interfaccia è se si verifica un errore di analisi nel codice di script in una pagina HTML, lo script DE Invia questa interfaccia a SDM, in modo che sia possibile visualizzare il documento con l'errore di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
