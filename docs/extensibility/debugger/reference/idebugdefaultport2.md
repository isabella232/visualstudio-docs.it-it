---
title: Proprietà IDebugDefaultPort2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732320"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Questa interfaccia fornisce diversi metodi per accedere alle funzionalità di notifica e server di una porta.

## <a name="syntax"></a>Sintassi

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per rappresentare la porta di debug per l'accesso ai programmi. Un fornitore di porta personalizzato può anche implementare questa interfaccia se gestisce il debug remoto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un argomento ai metodi sul [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaccia fornisce questa interfaccia. La chiamata [queryInterface](/cpp/atl/queryinterface) su un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia può anche ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi definiti in [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), questa interfaccia implementa i seguenti metodi:

|Metodo|Descrizione|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ottiene l'interfaccia di notifica della porta da questa porta.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ottiene l'interfaccia per il server che ospita questa porta.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se questa porta è in esecuzione nel computer locale.|

## <a name="remarks"></a>Osservazioni
 Il nome`IDebugDefaultPort2`" " è un po' un termine improprio, in quanto non rappresenta una porta predefinita. Potrebbe essere chiamato "IDebugPort3".

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
