---
description: Questa interfaccia viene utilizzata per notificare a Visual Studio le modifiche apportate al documento di origine fornite dal motore di debug.
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: edf7cd483b39fb1fb5dc182a08bbbca8295b2359
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094094"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Questa interfaccia viene utilizzata per notificare a Visual Studio le modifiche apportate al documento di origine fornite dal motore di debug.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per supportare apportare modifiche al codice sorgente. Questa interfaccia viene in genere implementata nello stesso oggetto che implementa l'interfaccia [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="notes-for-callers"></a>Note per i chiamanti
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ottiene questa interfaccia tramite una chiamata al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metodo. L' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia viene ottenuta da una chiamata al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> metodo. L' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia viene ottenuta chiamando il metodo [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugDocumentTextEvents2` .

|Metodo|Descrizione|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica che l'intero documento è stato eliminato definitivamente.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica al pacchetto di debug che il testo è stato inserito nel documento.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica al pacchetto di debug che il testo è stato rimosso dal documento.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica al pacchetto di debug che il testo è stato sostituito nel documento.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica al pacchetto di debug che gli attributi di testo sono stati aggiornati nel documento.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al destinatario dell'evento che gli attributi del documento sono stati aggiornati.|

## <a name="remarks"></a>Commenti
 Solo i motori di debug che forniscono i propri documenti possono sfruttare l' `IDebugDocumentTextEvent2` interfaccia. Un esempio è costituito da un motore di debug di script. Nel processo di interpretazione degli script, è possibile generare un nuovo codice sorgente che non è presente in alcun file su disco ed è noto solo per il DE.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
