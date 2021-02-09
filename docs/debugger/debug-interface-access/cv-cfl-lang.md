---
title: CV_CFL_LANG | Microsoft Docs
description: Ottenere informazioni sul tipo di enumerazione CV_CFL_LANG, che specifica il linguaggio del codice dell'applicazione o del modulo collegato in Debug Interface Access SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 46c20fbe0c46a6c964a05b92ccd3a8bcf73cd1f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857370"
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
CV_CFL_C lingua dell'applicazione è C.

CV_CFL_CXX linguaggio dell'applicazione è C++.

CV_CFL_FORTRAN lingua dell'applicazione è FORTRAN.

CV_CFL_MASM linguaggio applicazione è Microsoft Macro Assembler.

CV_CFL_PASCAL linguaggio di applicazione è Pascal.

CV_CFL_BASIC lingua dell'applicazione è di base.

CV_CFL_COBOL linguaggio dell'applicazione è COBOL.

CV_CFL_LINK applicazione è un modulo generato dal linker.

CV_CFL_CVTRES applicazione è un modulo di risorse convertito con lo strumento CVTRES.

CV_CFL_CVTPGD applicazione è un modulo ottimizzato con POGO generato con lo strumento CVTPGD.

CV_CFL_CSHARP linguaggio dell'applicazione è C#.

CV_CFL_VB lingua dell'applicazione è Visual Basic.

CV_CFL_ILASM linguaggio dell'applicazione è un assembly di linguaggio intermedio, ovvero un assembly CLR (Common Language Runtime).

CV_CFL_JAVA linguaggio dell'applicazione è Java.

CV_CFL_JSCRIPT linguaggio dell'applicazione è JScript.

CV_CFL_MSIL linguaggio dell'applicazione è un linguaggio MSIL (Microsoft Intermediate Language) sconosciuto, probabilmente il risultato dell'utilizzo dell'opzione [/LTCG (generazione codice in fase di collegamento)](/cpp/build/reference/ltcg-link-time-code-generation) .

CV_CFL_HLSL linguaggio applicazione è un linguaggio shader di alto livello.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_Language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
