---
description: Indica il protocollo utilizzato per comunicare tra un server di debug e il pacchetto di debug .
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0477aaed753523a1b6bde06c65e54c28bfe7922
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120166"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Indica il protocollo utilizzato per comunicare tra un server di debug e il pacchetto di debug .

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
Non è stata stabilita alcuna connessione a un server.

`CONNECTION_UNKNOWN`\
È stata stabilita una connessione, ma è di tipo sconosciuto.

`CONNECTION_LOCAL`\
La connessione è a un server locale.

`CONNECTION_PIPE`\
La connessione viene stabilita tramite un named pipe.

`CONNECTION_TCPIP`\
La connessione usa TCP/IP.

`CONNECTION_HTTP`\
La connessione usa HTTP (tramite un server Web).

`CONNECTION_OTHER`\
È stato stabilito un altro tipo di connessione (questo valore non è attualmente in uso).

## <a name="remarks"></a>Commenti
Questi valori vengono restituiti dal [metodo GetConnectionProtocol.](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
