---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf713ea542901cbde588600d40f144f0fae843e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718846"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Rappresenta una posizione in un file di origine da un offset di carattere.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementata dall'IDE e utilizzato dai motori di debug.

## <a name="methods"></a>Metodi
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentPositionOffset2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera l'intervallo per la posizione corrente del documento.|

## <a name="remarks"></a>Note
 Restituisce le stesse informazioni [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ma in `char` viene eseguito l'offset dall'inizio del documento. Questo presenta il documento, ad esempio che esisterebbe in un disco, vale a dire, una matrice unidimensionale di caratteri, anziché le informazioni di riga e colonna che viene in genere restituito.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)