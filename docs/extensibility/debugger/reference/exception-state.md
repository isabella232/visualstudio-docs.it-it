---
title: EXCEPTION_STATE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736952"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Specifica lo stato dell'eccezione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Campi
`EXCEPTION_NONE`\
Non arrestarsi in corrispondenza dell'eccezione.

`EXCEPTION_STOP_FIRST_CHANCE`\
Stop al primo sputo di eccezione. Quando si descrive un evento di eccezione, questo flag indica che l'evento di eccezione è un evento di eccezione first-chance.

`EXCEPTION_STOP_SECOND_CHANCE`\
Arresto al secondo attivazione di eccezione. Quando si descrive un evento di eccezione, indica che l'evento di eccezione è un evento di eccezione second-chance.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Interrompere la prima generazione di un'eccezione in modalità utente. Quando si descrive un evento di eccezione, indica che l'evento di eccezione è un evento di eccezione utente di prima possibilità.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Interrompere quando non viene rilevata un'eccezione in modalità utente. Quando si descrive un evento di eccezione, indica che l'evento di eccezione è un evento di eccezione non rilevata dalla modalità utente.

`EXCEPTION_STOP_ALL`\
Interrompere in caso di qualsiasi eccezione. Non utilizzato durante la descrizione di un evento di eccezione.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Quando si descrive un evento di eccezione, indica che l'eccezione non può continuare da.

`EXCEPTION_CODE_SUPPORTED`\
Indica che l'eccezione contiene codice che lo supporta. Utilizzato nella visualizzazione di un'eccezione

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Indica che il codice di eccezione deve essere visualizzato in esadecimale. Utilizzato nella visualizzazione di un'eccezione.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Indica che il codice di eccezione supporta JustMyCode. Utilizzato nella visualizzazione di un'eccezione.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Indica che il debugger del codice gestito deve gestire le eccezioni. Se non è impostato, il debugger predefinito gestisce le eccezioni. Viene passato al metodo [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) e non utilizzato nella struttura [EXCEPTION_INFO.](../../../extensibility/debugger/reference/exception-info.md)

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NON UTILIZZARE.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NON UTILIZZARE.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NON UTILIZZARE.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NON UTILIZZARE.

## <a name="remarks"></a>Osservazioni
Utilizzato come `dwState` membro della struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) per indicare lo stato dell'eccezione e le operazioni che è possibile eseguire al riguardo.

Questi valori vengono inoltre passati al metodo [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) per impostare lo stato di tutte le eccezioni.

Questi flag possono essere combinati con un OR bit per bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
