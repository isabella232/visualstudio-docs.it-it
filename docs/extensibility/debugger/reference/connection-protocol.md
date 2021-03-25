---
description: Indica il protocollo utilizzato per la comunicazione tra un server di debug e il pacchetto di debug (DE).
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d514b9aa0e37e90e99f21b5b4906cff9d32472db
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059496"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Indica il protocollo utilizzato per la comunicazione tra un server di debug e il pacchetto di debug (DE).

## <a name="syntax"></a>Sintassi

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Campi
`CONNECTION_NONE`\
Non è stata effettuata alcuna connessione a un server.

`CONNECTION_UNKNOWN`\
È stata effettuata una connessione, ma è di tipo sconosciuto.

`CONNECTION_LOCAL`\
Connessione a un server locale.

`CONNECTION_PIPE`\
La connessione viene stnamed pipe.

`CONNECTION_TCPIP`\
La connessione utilizza TCP/IP.

`CONNECTION_HTTP`\
La connessione Usa HTTP (tramite un server Web).

`CONNECTION_OTHER`\
È stato stabilito un altro tipo di connessione (questo valore non è attualmente in uso).

## <a name="remarks"></a>Commenti
Questi valori vengono restituiti dal metodo [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
