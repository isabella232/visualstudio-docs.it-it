---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699353"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica il linguaggio del codice sorgente dell'applicazione o del modulo collegato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 CV_CFL_C  
 La lingua dell'applicazione è C.  
  
 CV_CFL_CXX  
 La lingua dell'applicazione è C++.  
  
 CV_CFL_FORTRAN  
 La lingua dell'applicazione è FORTRAN.  
  
 CV_CFL_MASM  
 La lingua dell'applicazione è Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Il linguaggio dell'applicazione è Pascal.  
  
 CV_CFL_BASIC  
 La lingua dell'applicazione è di base.  
  
 CV_CFL_COBOL  
 La lingua dell'applicazione è COBOL.  
  
 CV_CFL_LINK  
 L'applicazione è un modulo generato dal linker.  
  
 CV_CFL_CVTRES  
 L'applicazione è un modulo di risorse convertito con lo strumento CVTRES.  
  
 CV_CFL_CVTPGD  
 L'applicazione è un modulo ottimizzato con POGO generato con lo strumento CVTPGD.  
  
 CV_CFL_CSHARP  
 La lingua dell'applicazione è C#.  
  
 CV_CFL_VB  
 La lingua dell'applicazione è Visual Basic.  
  
 CV_CFL_ILASM  
 La lingua dell'applicazione è l'assembly del linguaggio intermedio, ovvero l'assembly Common Language Runtime (CLR).  
  
 CV_CFL_JAVA  
 La lingua dell'applicazione è Java.  
  
 CV_CFL_JSCRIPT  
 Il linguaggio dell'applicazione è JScript.  
  
 CV_CFL_MSIL  
 La lingua dell'applicazione è un linguaggio MSIL (Microsoft Intermediate Language) sconosciuto, probabilmente il risultato dell'utilizzo dell'opzione [/LTCG (generazione codice in fase di collegamento)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) .  
  
 CV_CFL_HLSL  
 La lingua dell'applicazione è High Level Shader Language.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_Language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst. h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
