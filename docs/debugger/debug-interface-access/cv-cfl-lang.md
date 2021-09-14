---
title: CV_CFL_LANG | Microsoft Docs
description: Ottenere informazioni sul tipo CV_CFL_LANG di enumerazione, che specifica il linguaggio di codice dell'applicazione o del modulo collegato nell'SDK di accesso all'interfaccia di debug.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8bb3192316bf3dbdda7ee06f9bfa9a159ab8d982
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630683"
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
CV_CFL_C linguaggio dell'applicazione è C.

CV_CFL_CXX linguaggio applicativo è C++.

CV_CFL_FORTRAN linguaggio applicativo èRAN.

CV_CFL_MASM linguaggio dell'applicazione è Microsoft Macro Assembler.

CV_CFL_PASCAL linguaggio dell'applicazione è Pascal.

CV_CFL_BASIC linguaggio applicativo è BASIC.

CV_CFL_COBOL linguaggio dell'applicazione è COBOL.

CV_CFL_LINK'applicazione è un modulo generato dal linker.

CV_CFL_CVTRES application è un modulo di risorse convertito con lo strumento CVTRES.

CV_CFL_CVTPGD application è un modulo ottimizzato per POGO generato con lo strumento CVTPGD.

CV_CFL_CSHARP linguaggio applicativo è C#.

CV_CFL_VB linguaggio dell'applicazione Visual Basic.

CV_CFL_ILASM Application Language è un assembly di linguaggio intermedio, ovvero un assembly CLR (Common Language Runtime).

CV_CFL_JAVA linguaggio applicativo è Java.

CV_CFL_JSCRIPT linguaggio applicativo è Jscript.

CV_CFL_MSIL linguaggio applicativo è un linguaggio MSIL (Microsoft Intermediate Language) sconosciuto, probabilmente il risultato dell'uso dell'opzione [/LTCG (generazione](/cpp/build/reference/ltcg-link-time-code-generation) di codice in fase di collegamento).

CV_CFL_HLSL linguaggio dell'applicazione è il linguaggio shader di alto livello.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti da una chiamata al [metodo IDiaSymbol::get_language.](../../debugger/debug-interface-access/idiasymbol-get-language.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
