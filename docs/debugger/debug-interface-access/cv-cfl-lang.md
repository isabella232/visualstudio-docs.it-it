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
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745342"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
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
La lingua dell'applicazione CV_CFL_C è C.

La lingua dell'applicazione C++CV_CFL_CXX è.

La lingua dell'applicazione CV_CFL_FORTRAN è FORTRAN.

CV_CFL_MASM Application Language è Microsoft Macro Assembler.

Il linguaggio dell'applicazione CV_CFL_PASCAL è Pascal.

La lingua dell'applicazione CV_CFL_BASIC è di base.

Il linguaggio dell'applicazione CV_CFL_COBOL è COBOL.

L'applicazione CV_CFL_LINK è un modulo generato dal linker.

L'applicazione CV_CFL_CVTRES è un modulo di risorse convertito con lo strumento CVTRES.

L'applicazione CV_CFL_CVTPGD è un modulo ottimizzato con POGO generato con lo strumento CVTPGD.

La lingua dell'applicazione C#CV_CFL_CSHARP è.

La lingua dell'applicazione CV_CFL_VB è Visual Basic.

CV_CFL_ILASM Application Language è un assembly di linguaggio intermedio, ovvero un assembly Common Language Runtime (CLR).

La lingua dell'applicazione CV_CFL_JAVA è Java.

Il linguaggio dell'applicazione CV_CFL_JSCRIPT è JScript.

La lingua dell'applicazione CV_CFL_MSIL è un linguaggio MSIL (Microsoft Intermediate Language) sconosciuto, probabilmente il risultato dell'utilizzo dell'opzione [/LTCG (generazione di codice in fase di collegamento)](/cpp/build/reference/ltcg-link-time-code-generation) .

La lingua dell'applicazione CV_CFL_HLSL è il linguaggio shader di alto livello.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_Language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
