---
title: BasicType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580837"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica il tipo di base del simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elementi  
 btNoType  
 Nessun tipo di base specificato.  
  
 btVoid  
 Il tipo di base è `void` .  
  
 btChar  
 Il tipo di base è un `char` (tipo C/C++).  
  
 btWChar  
 Il tipo di base è un carattere wide (Unicode) ( `WCHAR` ).  
  
 btInt  
 Il tipo di base è `signed int` (tipo C/C++).  
  
 btUInt  
 Il tipo di base è `unsigned int` (tipo C/C++).  
  
 btFloat  
 Il tipo di base è un numero a virgola mobile ( `FLOAT` ).  
  
 btBCD  
 Il tipo di base è un valore decimale con codifica binaria ( `BCD` ).  
  
 btBool  
 Il tipo di base è un valore booleano ( `BOOL` ).  
  
 btLong  
 Il tipo di base è un `long int` (tipo C/C++).  
  
 btULong  
 Il tipo di base è un `unsigned long int` tipo (C/C++).  
  
 btCurrency  
 Il tipo di base è Currency.  
  
 btDate  
 Il tipo di base è date/time ( `DATE` ).  
  
 btVariant  
 Il tipo di base è una struttura di tipo variabile ( `VARIANT` ).  
  
 btComplex  
 Il tipo di base è un numero complesso.  
  
 btBit  
 Il tipo di base è un bit.  
  
 btBSTR  
 Il tipo di base è una stringa di base o binaria ( `BSTR` ).  
  
 btHresult  
 Il tipo di base è `HRESULT` .  
  
## <a name="remarks"></a>Osservazioni  
 I valori di questa enumerazione vengono restituiti dal metodo [IDiaSymbol:: get_BaseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst. h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
