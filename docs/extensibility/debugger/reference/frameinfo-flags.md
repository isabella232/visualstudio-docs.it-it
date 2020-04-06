---
title: FRAMEINFO_FLAGS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736805"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Specifica le informazioni da recuperare su un oggetto stack frame.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Campi
`FIF_FUNCNAME`\
Inizializzare/utilizzare `m_bstrFuncName` il campo.

`FIF_RETURNTYPE`\
Inizializzare/utilizzare `m_bstrReturnType` il campo.

`FIF_ARGS`\
Inizializzare/utilizzare `m_bstrArgs` il campo.

`FIF_LANGUAGE`\
Inizializzare/utilizzare `m_bstrLanguage` il campo.

`FIF_MODULE`\
Inizializzare/utilizzare `m_bstrModule` il campo.

`FIF_STACKRANGE`\
Inizializzare/utilizzare `m_addrMin` `m_addrMax` i campi e (intervallo di stack).

`FIF_FRAME`\
Inizializzare/utilizzare `m_pFrame` il campo.

`FIF_DEBUGINFO`\
Inizializzare/utilizzare `m_fHasDebugInfo` il campo.

`FIF_STALECODE`\
Inizializzare/utilizzare `m_fStaleCode` il campo.

`FIF_ANNOTATEDFRAME`\
Inizializzare/utilizzare `m_fAnnotatedFrame` il campo.

`FIF_DEBUG_MODULEP`\
Inizializzare/utilizzare `m_pModule` il campo.

`FIF_FUNCNAME_FORMAT`\
Formatta il nome della funzione. Il risultato viene `m_bstrFunName` restituito nel campo e non vengono compilati altri campi.

`FIF_FUNCNAME_RETURNTYPE`\
Aggiunge il tipo `m_bstrFuncName` restituito al campo.

`FIF_FUNCNAME_ARGS`\
Aggiunge gli argomenti `m_bstrFuncName` al campo.

`FIF_FUNCNAME_LANGUAGE`\
Aggiunge la lingua `m_bstrFuncName` al campo.

`FIF_FUNCNAME_MODULE`\
Aggiunge il nome `m_bstrFuncName` del modulo al campo.

`FIF_FUNCNAME_LINES`\
Aggiunge il numero di `m_bstrFuncName` righe al campo.

`FIF_FUNCNAME_OFFSET`\
Aggiunge al `m_bstrFuncName` campo l'offset in byte dall'inizio della riga, se `FIF_FUNCNAME_LINES` specificato. Se `FIF_FUNCNAME_LINES` non viene specificato o se i numeri di riga non sono disponibili, aggiunge l'offset in byte dall'inizio della funzione.

`FIF_FUNCNAME_ARGS_TYPES`\
Aggiunge il tipo di ogni `m_bstrFuncName` argomento di funzione al campo.

`FIF_FUNCNAME_ARGS_NAMES`\
Aggiunge il nome di ogni `m_bstrFuncName` argomento di funzione al campo.

`FIF_FUNCNAME_ARGS_VALUES`\
Aggiunge il valore di ogni `m_bstrFuncName` argomento di funzione al campo.

`FIF_FUNCNAME_ARGS_ALL`\
Aggiunge il tipo, il nome e `m_bstrFuncName` il valore di tutti gli argomenti al campo.

`FIF_ARGS_TYPES`\
I tipi di argomento vengono recuperati e formattati.

`FIF_ARGS_NAMES`\
I nomi degli argomenti vengono recuperati e formattati.

`FIF_ARGS_VALUES`\
I valori degli argomenti vengono recuperati e formattati.

`FIF_ARGS_ALL`\
Recuperare e formattare il tipo, il nome e il valore di tutti gli argomenti.

`FIF_ARGS_NOFORMAT`\
Specifica che gli argomenti non vengono formattati (ad esempio, non aggiungere parentesi di apertura e chiusura intorno all'elenco di argomenti né aggiungere un separatore tra gli argomenti).

`FIF_ARGS_NO_FUNC_EVAL`\
Specifica che la valutazione della funzione (proprietà) non deve essere utilizzata durante il recupero dei valori degli argomenti.

`FIF_FILTER_NON_USER_CODE`\
Il motore di debug consente di filtrare i frame di codice non utente in modo che non siano inclusi.

`FIF_ARGS_NO_TOSTRING`\
Non consentire `ToString()` la valutazione o la formattazione della funzione quando si restituiscono argomenti di funzione.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Le informazioni sui frame devono essere ottenute dal dominio dell'app ospitata anziché dal processo di hosting.

## <a name="remarks"></a>Osservazioni
Questi flag vengono passati ai metodi [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) e [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) per indicare i campi da inizializzare nella struttura o nelle strutture [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

Questi flag vengono utilizzati anche per indicare quali campi della struttura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) vengono utilizzati e validi quando viene restituita la struttura. Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
