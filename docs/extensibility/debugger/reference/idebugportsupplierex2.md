---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9a0958614c8df326c20ad8030bb798447a5e62a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840158"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Fornisce supporto per un fornitore di porte per la selezione e l'interazione con un server di base.

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia in modo che sia in grado di selezionare il server principale da usare.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di **IDebugPortSupplierEx2**.

|Metodo|Descrizione|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Imposta il server principale per il fornitore della porta.|

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
