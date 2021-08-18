---
description: Rappresenta una posizione in un file di origine come offset di caratteri.
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f6fdb3fc220a4495146ad9ca66e4b2cee73f1909
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119437"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Rappresenta una posizione in un file di origine come offset di caratteri.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dall'IDE e utilizzato dai motori di debug.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono illustrati i metodi di `IDebugDocumentPositionOffset2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera l'intervallo per la posizione corrente del documento.|

## <a name="remarks"></a>Commenti
 Vengono restituite le stesse informazioni di [GetRange,](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ma in `char` offset dall'inizio del documento. Il documento viene presentato come se fosse presente su un disco, ad esempio una matrice unidimensionale di caratteri, anziché le informazioni su riga e colonna normalmente restituite.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
