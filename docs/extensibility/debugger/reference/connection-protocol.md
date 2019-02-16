---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dcf3d271d331664d6d2ef210868245b50c264d6
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316484"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Indica il protocollo usato per la comunicazione tra un server di debug e il pacchetto di debug (DE).

## <a name="syntax"></a>Sintassi

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

#### <a name="parameters"></a>Parametri
CONNECTION_NONE  
Non è stata stabilita alcuna connessione a un server.

CONNECTION_UNKNOWN  
È stata stabilita una connessione, ma è di tipo sconosciuto.

CONNECTION_LOCAL  
Connessione è a un server locale.

CONNECTION_PIPE  
Connessione avviene tramite una named pipe.

CONNECTION_TCPIP  
Connessione Usa TCP/IP.

CONNECTION_HTTP  
Connessione utilizza HTTP (tramite un server Web).

CONNECTION_OTHER  
Un altro tipo di connessione è stato stabilito (questo valore non viene attualmente utilizzato).

## <a name="remarks"></a>Note
Questi valori vengono restituiti dai [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
