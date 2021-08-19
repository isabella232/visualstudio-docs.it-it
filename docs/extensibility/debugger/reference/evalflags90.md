---
description: Enumera i valori validi per i flag che controllano la valutazione dell'espressione.
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7d4916f5070792b7169303060b078acca422ef2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153394"
---
# <a name="evalflags90"></a>EVALFLAGS90
Enumera i valori validi per i flag che controllano la valutazione dell'espressione. Questa enumerazione estende [l'enumerazione EVALFLAGS.](../../../extensibility/debugger/reference/evalflags.md)

## <a name="syntax"></a>Sintassi

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Campi
`EVAL90_RETURNVALUE`\
Specifica che il valore restituito, se presente, deve essere valutato.

`EVAL90_NOSIDEEFFECTS`\
Specifica che gli effetti collaterali non sono consentiti.

`EVAL90_ALLOWBPS`\
Specifica l'arresto in corrispondenza dei punti di interruzione.

`EVAL90_ALLOWERRORREPORT`\
Specifica che la segnalazione degli errori all'host deve essere consentita. Usato principalmente per la valutazione delle espressioni nello script in Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Forza la valutazione delle funzioni come indirizzi, anziché richiamare la funzione.

`EVAL90_NOFUNCEVAL`\
Impedisce la valutazione della funzione. Si consideri ad esempio `int` il token nell'espressione `myExpression(int) + 10` . Questa funzione può essere valutata correttamente come indirizzo, ma non come valore.

`EVAL90_NOEVENTS`\
Flag per indicare che gli eventi che si verificano durante la valutazione dell'espressione non devono essere inviati alla gestione del debug di sessione (SDM) o all'IDE.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Abilita la valutazione delle espressioni in fase di progettazione.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Consente la creazione implicita di variabili.

`EVAL90_FORCE_EVALUATION_NOW`\
Forza l'esecuzione immediata della valutazione. Ciò è utile quando si esegue una richiesta, ad esempio una richiesta dell'utente.

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg90.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
