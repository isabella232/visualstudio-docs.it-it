---
description: Questa interfaccia rappresenta un documento di testo.
title: Interfaccia IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa88c04333243ba016477e98a216bf957616ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119412"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Questa interfaccia rappresenta un documento di testo.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug implementa questa interfaccia quando il codice sorgente che deve fornire è in formato testo. Poiché si tratta del caso più tipico, se un'interfaccia DE implementa [l'interfaccia IDebugDocument2,](../../../extensibility/debugger/reference/idebugdocument2.md) deve implementare anche l'interfaccia `IDebugDocumentText2` .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare il `QueryInterface` metodo per ottenere questa interfaccia da un'interfaccia `IDebugDocument2` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nell'interfaccia `IDebugDocument2` , questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera le dimensioni del testo in questa posizione nel documento.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera il testo dalla posizione specificata nel documento.|

## <a name="remarks"></a>Commenti
 Un oggetto che implementa questa interfaccia deve implementare anche l'interfaccia , che fornisce <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> l'interfaccia per un oggetto <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugDocumentTextEvents2.](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
