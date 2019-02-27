---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f02545f1c19b57e46af302fbc0b2abaa7445612
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646343"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Specifica il linguaggio del codice sorgente dell'applicazione o del modulo collegato.

## <a name="syntax"></a>Sintassi

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Elementi
Lingua dell'applicazione CV_CFL_C è sufficiente.

Lingua dell'applicazione CV_CFL_CXX è C++.

Lingua dell'applicazione CV_CFL_FORTRAN è FORTRAN.

Lingua dell'applicazione CV_CFL_MASM è Microsoft Macro Assembler.

Lingua dell'applicazione CV_CFL_PASCAL è la convenzione Pascal.

Lingua dell'applicazione CV_CFL_BASIC è BASIC.

Lingua dell'applicazione CV_CFL_COBOL è COBOL.

Applicazione CV_CFL_LINK è un modulo generate dal linker.

Applicazione CV_CFL_CVTRES è un modulo di risorse convertito con lo strumento CVTRES.

Applicazione CV_CFL_CVTPGD è un modulo POGO ottimizzato generato con lo strumento CVTPGD.

Lingua dell'applicazione CV_CFL_CSHARP è C#.

Lingua dell'applicazione CV_CFL_VB è Visual Basic.

Lingua dell'applicazione CV_CFL_ILASM è assembly intermediate language (vale a dire assembly Common Language Runtime (CLR)).

Lingua dell'applicazione CV_CFL_JAVA è Java.

Lingua dell'applicazione CV_CFL_JSCRIPT è Jscript.

Lingua dell'applicazione CV_CFL_MSIL è un sconosciuto linguaggio MSIL (Microsoft Intermediate), probabilmente un risultato dell'uso di [/LTCG (generazione di codice in fase di collegamento)](/cpp/build/reference/ltcg-link-time-code-generation) passare.

Lingua dell'applicazione CV_CFL_HLSL è High Level Shader Language.

## <a name="remarks"></a>Osservazioni
I valori di questa enumerazione vengono restituiti da una chiamata per il [Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
