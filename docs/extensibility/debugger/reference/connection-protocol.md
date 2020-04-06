---
title: CONNECTION_PROTOCOL . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737643"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Indica il protocollo utilizzato per comunicare tra un server di debug e il pacchetto di debug (DE).

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

## <a name="fields"></a>Campi
`CONNECTION_NONE`\
Non è stata stabilita alcuna connessione a un server.

`CONNECTION_UNKNOWN`\
È stata stabilita una connessione, ma è di tipo sconosciuto.

`CONNECTION_LOCAL`\
La connessione è a un server locale.

`CONNECTION_PIPE`\
La connessione è tramite una named pipe.

`CONNECTION_TCPIP`\
La connessione utilizza TCP/IP.

`CONNECTION_HTTP`\
La connessione utilizza HTTP (tramite un server Web).

`CONNECTION_OTHER`\
È stato stabilito un altro tipo di connessione (questo valore non è attualmente utilizzato).

## <a name="remarks"></a>Osservazioni
Questi valori vengono restituiti dal [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) metodo.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
