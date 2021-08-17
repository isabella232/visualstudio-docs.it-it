---
description: Il motore di debug usa questa interfaccia per richiedere il caricamento di un documento.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5eeae3a29c4e0fdfaad3808228ce6bed9cfe3d7ff2f6e56f0699ed4e051d64df
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434230"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Il motore di debug usa questa interfaccia per richiedere il caricamento di un documento.

## <a name="syntax"></a>Sintassi

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il de implementa questa interfaccia quando è necessario aprire un file di origine. Questa interfaccia viene implementata solo dai motori di debug che funzionano con o fanno parte di interpreti di script. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (SDM usa [QueryInterface](/cpp/atl/queryinterface) per accedere all'interfaccia). `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento quando deve avere aperto un file di origine. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugActivateDocumentEvent2` .

|Metodi|Descrizione|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Ottiene il documento da attivare.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Ottiene il contesto del documento che descrive la posizione all'interno del documento.|

## <a name="remarks"></a>Commenti
 Uno scenario tipico in cui questa interfaccia viene usata è se si verifica un errore di analisi nel codice di script in una pagina HTML, lo script DE invia questa interfaccia a SDM in modo che il documento con l'errore di analisi possa essere visualizzato.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
