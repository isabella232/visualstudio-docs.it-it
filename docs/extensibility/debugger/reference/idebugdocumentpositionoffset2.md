---
title: Proprietà IDebugDocumentPositionOffset2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731606"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Rappresenta una posizione in un file di origine come offset di carattere.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dall'IDE e utilizzato dai motori di debug.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono `IDebugDocumentPositionOffset2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera l'intervallo per la posizione corrente del documento.|

## <a name="remarks"></a>Osservazioni
 Restituisce le stesse informazioni di `char` [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ma negli offset dall'inizio del documento. In questo modo il documento viene presentata come se esistesse su un disco, ovvero una matrice unidimensionale di caratteri, anziché le informazioni di riga e colonna che vengono normalmente restituite.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
