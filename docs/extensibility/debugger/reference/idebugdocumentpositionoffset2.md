---
description: Rappresenta una posizione in un file di origine come offset carattere.
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01815a7dcae5a469db20b9288918b4e2aaf9ffed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066321"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Rappresenta una posizione in un file di origine come offset carattere.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dall'IDE e utilizzato dai motori di debug.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugDocumentPositionOffset2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera l'intervallo per la posizione del documento corrente.|

## <a name="remarks"></a>Commenti
 Restituisce le stesse informazioni di [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ma in `char` offset dall'inizio del documento. Viene visualizzato il documento come se fosse presente su un disco, ovvero una matrice unidimensionale di caratteri, anziché le informazioni di riga e colonna restituite normalmente.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
