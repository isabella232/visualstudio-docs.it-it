---
description: Specifica le informazioni da recuperare su un oggetto stack frame dati.
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c51d36ca9900731f816961f4cedf362762d26c5267666bbe5c3135d730dbd85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403195"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Specifica le informazioni da recuperare su un oggetto stack frame dati.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_FRAMEINFO_FLAGS {
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
public enum enum_FRAMEINFO_FLAGS {
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
Inizializzare/usare il `m_bstrFuncName` campo .

`FIF_RETURNTYPE`\
Inizializzare/usare il `m_bstrReturnType` campo .

`FIF_ARGS`\
Inizializzare/usare il `m_bstrArgs` campo .

`FIF_LANGUAGE`\
Inizializzare/usare il `m_bstrLanguage` campo .

`FIF_MODULE`\
Inizializzare/usare il `m_bstrModule` campo .

`FIF_STACKRANGE`\
Inizializzare/usare `m_addrMin` i campi e `m_addrMax` (intervallo dello stack).

`FIF_FRAME`\
Inizializzare/usare il `m_pFrame` campo .

`FIF_DEBUGINFO`\
Inizializzare/usare il `m_fHasDebugInfo` campo .

`FIF_STALECODE`\
Inizializzare/usare il `m_fStaleCode` campo .

`FIF_ANNOTATEDFRAME`\
Inizializzare/usare il `m_fAnnotatedFrame` campo .

`FIF_DEBUG_MODULEP`\
Inizializzare/usare il `m_pModule` campo .

`FIF_FUNCNAME_FORMAT`\
Formatta il nome della funzione. Il risultato viene `m_bstrFunName` restituito nel campo e non vengono compilati altri campi.

`FIF_FUNCNAME_RETURNTYPE`\
Aggiunge il tipo restituito al `m_bstrFuncName` campo.

`FIF_FUNCNAME_ARGS`\
Aggiunge gli argomenti al `m_bstrFuncName` campo.

`FIF_FUNCNAME_LANGUAGE`\
Aggiunge la lingua al `m_bstrFuncName` campo.

`FIF_FUNCNAME_MODULE`\
Aggiunge il nome del modulo al `m_bstrFuncName` campo.

`FIF_FUNCNAME_LINES`\
Aggiunge il numero di righe al `m_bstrFuncName` campo.

`FIF_FUNCNAME_OFFSET`\
Aggiunge al campo `m_bstrFuncName` l'offset in byte dall'inizio della riga, `FIF_FUNCNAME_LINES` se specificato. Se non viene specificato o se i numeri di riga `FIF_FUNCNAME_LINES` non sono disponibili, aggiunge l'offset in byte dall'inizio della funzione.

`FIF_FUNCNAME_ARGS_TYPES`\
Aggiunge il tipo di ogni argomento della funzione al `m_bstrFuncName` campo.

`FIF_FUNCNAME_ARGS_NAMES`\
Aggiunge il nome di ogni argomento della funzione al `m_bstrFuncName` campo.

`FIF_FUNCNAME_ARGS_VALUES`\
Aggiunge il valore di ogni argomento della funzione al `m_bstrFuncName` campo.

`FIF_FUNCNAME_ARGS_ALL`\
Aggiunge il tipo, il nome e il valore di tutti gli argomenti al `m_bstrFuncName` campo.

`FIF_ARGS_TYPES`\
I tipi di argomento vengono recuperati e formattati.

`FIF_ARGS_NAMES`\
I nomi degli argomenti vengono recuperati e formattati.

`FIF_ARGS_VALUES`\
I valori degli argomenti vengono recuperati e formattati.

`FIF_ARGS_ALL`\
Recuperare e formattare il tipo, il nome e il valore di tutti gli argomenti.

`FIF_ARGS_NOFORMAT`\
Specifica che gli argomenti non devono essere formattati, ad esempio non aggiungere parentesi di apertura e chiusura intorno all'elenco di argomenti né aggiungere un separatore tra gli argomenti.

`FIF_ARGS_NO_FUNC_EVAL`\
Specifica che la valutazione della funzione (proprietà) non deve essere usata durante il recupero dei valori degli argomenti.

`FIF_FILTER_NON_USER_CODE`\
Il motore di debug consente di filtrare i frame di codice non utente in modo che non siano inclusi.

`FIF_ARGS_NO_TOSTRING`\
Non consentire la valutazione `ToString()` o la formattazione delle funzioni quando vengono restituiti argomenti di funzione.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Le informazioni sui frame devono essere derivate dal dominio app ospitato anziché dal processo di hosting.

## <a name="remarks"></a>Commenti
Questi flag vengono passati ai metodi [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) e [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) per indicare quali campi devono essere inizializzati nella struttura o nelle strutture [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

Questi flag vengono usati anche per indicare quali campi della [struttura FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) vengono usati e validi quando viene restituita la struttura . Questi valori possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
