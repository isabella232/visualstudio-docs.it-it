---
description: Specifica lo stato dell'eccezione.
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33c7f939a8f630592890c3c03be662099680e64b87d4179425497ee864a6718c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262516"
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
Arrestarsi alla prima generazione dell'eccezione. Quando si descrive un evento di eccezione, questo flag indica che l'evento di eccezione è un evento di eccezione first-chance.

`EXCEPTION_STOP_SECOND_CHANCE`\
Arresto alla seconda generazione dell'eccezione. Quando si descrive un evento di eccezione, indica che l'evento di eccezione è un evento di eccezione second-chance.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Arrestarsi alla prima generazione di un'eccezione in modalità utente. Quando si descrive un evento di eccezione, indica che l'evento di eccezione è un evento di eccezione utente first-chance.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Arresta quando non viene rilevata un'eccezione in modalità utente. Quando si descrive un evento di eccezione, indica che l'evento di eccezione è un evento di eccezione in modalità utente non rilevata.

`EXCEPTION_STOP_ALL`\
Arresto in caso di eccezioni. Non utilizzato quando si descrive un evento di eccezione.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Quando si descrive un evento di eccezione, indica che l'eccezione non può essere continuata.

`EXCEPTION_CODE_SUPPORTED`\
Indica che l'eccezione include codice che la supporta. Usato nella visualizzazione di un'eccezione

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Indica che il codice dell'eccezione deve essere visualizzato in formato esadecimale. Utilizzato nella visualizzazione di un'eccezione.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Indica che il codice dell'eccezione supporta JustMyCode. Utilizzato nella visualizzazione di un'eccezione.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Indica che il debugger di codice gestito deve gestire le eccezioni. Se non è impostato, il debugger predefinito gestisce le eccezioni. Viene passato al [metodo SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) e non viene usato nella [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura .

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NON USARE.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NON USARE.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NON USARE.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NON USARE.

## <a name="remarks"></a>Commenti
Usato come membro della struttura EXCEPTION_INFO per indicare lo stato dell'eccezione e le relative `dwState` funzioni. [](../../../extensibility/debugger/reference/exception-info.md)

Questi valori vengono passati anche al [metodo SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) per impostare lo stato di tutte le eccezioni.

Questi flag possono essere combinati con un'operazione OR bit per bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
