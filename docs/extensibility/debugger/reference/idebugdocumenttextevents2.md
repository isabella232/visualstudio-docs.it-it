---
title: Proprietà IDebugDocumentTextEvents2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731371"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Questa interfaccia viene utilizzata per notificare a Visual Studio le modifiche al documento di origine fornite dal motore di debug.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per supportare la modifica delle modifiche al codice sorgente. Questa interfaccia viene in genere implementata sullo stesso oggetto che implementa il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]ottiene questa interfaccia tramite <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> una chiamata al metodo . L'interfaccia <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> viene ottenuta <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> da una chiamata al metodo . L'interfaccia <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> viene ottenuta chiamando il [QueryInterface](/cpp/atl/queryinterface) metodo su un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugDocumentTextEvents2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica che l'intero documento è stato eliminato.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica al pacchetto di debug che il testo è stato inserito nel documento.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica al pacchetto di debug che il testo è stato rimosso dal documento.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica al pacchetto di debug che il testo è stato sostituito nel documento.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica al pacchetto di debug che gli attributi di testo sono stati aggiornati nel documento.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica al destinatario l'evento che gli attributi del documento sono stati aggiornati.|

## <a name="remarks"></a>Osservazioni
 Solo i motori di debug che forniscono `IDebugDocumentTextEvent2` i propri documenti svantaggierebbero l'interfaccia. Un esempio di questo potrebbe essere un motore di debug di scripting. Nel processo di interpretazione degli script, è possibile generare nuovo codice sorgente che non è presente in alcun file su disco ed è noto solo al DE.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
