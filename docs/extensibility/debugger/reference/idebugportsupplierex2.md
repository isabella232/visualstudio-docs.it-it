---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bebf232e17df54d4dae2392a40f2ccbc3fc711c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353308"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Fornisce supporto per un fornitore di porte selezionare e interagire con un server core.

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia in modo che è possibile selezionare il server core da usare.

## <a name="methods"></a>Metodi
 Nella tabella seguente sono illustrati i metodi di **IDebugPortSupplierEx2**.

|Metodo|Descrizione|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Imposta il server principale per il fornitore della porta.|

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)