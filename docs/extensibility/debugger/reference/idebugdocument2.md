---
description: Questa interfaccia rappresenta un documento di origine.
title: Interfaccia IDebugDocument2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8bc5fcca187603ab4001e38df67eacf0df5b1be80353aa161bc921a3a3fd1b22
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434009"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Questa interfaccia rappresenta un documento di origine.

## <a name="syntax"></a>Sintassi

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] in genere implementa questa interfaccia. Un motore di debug può implementare questa interfaccia anche quando deve fornire il codice sorgente e l'origine non esiste su disco.  In questi casi, dedi implementerebbe anche le interfacce [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) e [IDebugActivateDocumentEvent2,](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) nonché alcuni metodi aggiuntivi nelle [interfacce IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) e [IDebugDocumentPosition2.](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi nelle `IDebugDocumentContext2` interfacce , , e `IDebugDisassemblyStream2` `IDebugDocumentPosition2` `IDebugActivateDocumentEvent2` restituiscono questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugDocument2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ottiene il nome del documento in uno dei diversi formati.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ottiene l'identificatore di classe del documento.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene implementata solo quando il DE fornisce il codice sorgente. Ad esempio, quando si esegue il debug di script in una pagina HTML, il de fornisce il codice sorgente perché l'origine viene scaricata o generata dinamicamente e non esiste come file su disco. Quando si esegue il debug di linguaggi tradizionali, ad esempio C++, questa interfaccia non deve essere implementata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
