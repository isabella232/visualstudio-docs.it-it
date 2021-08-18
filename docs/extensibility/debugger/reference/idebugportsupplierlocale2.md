---
description: Fornisce il supporto delle impostazioni locali per un fornitore di porte.
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fb273e38e207f36f7d438b7fba0bfe093f1c8344
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088016"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Fornisce il supporto delle impostazioni locali per un fornitore di porte.

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia per impostare le impostazioni locali.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di **IDebugPortSupplierLocale2.**

|Metodo|Descrizione|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Imposta le impostazioni locali per il fornitore della porta.|

## <a name="requirements"></a>Requisiti
 Intestazione: Portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
