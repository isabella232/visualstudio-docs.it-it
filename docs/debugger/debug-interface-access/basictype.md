---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 891b83d6a43cb73fe8f38bb8b20201cbcfa230f6
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154082"
---
# <a name="basictype"></a>BasicType
Specifica tipo di base del simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
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
   btHresult  = 31,  
   btChar16   = 32,  // char16_t
   btChar32   = 33,  // char32_t
};  
```  
  
## <a name="elements"></a>Elementi  
 btNoType  
 Viene specificato alcun tipo di base.  
  
 btVoid  
 Tipo di base è un `void`.  
  
 btChar  
 Tipo di base è un `char` (tipo di C/C++).  
  
 btWChar  
 Tipo di base è un carattere wide (Unicode) (`WCHAR`).  
  
 btInt  
 Tipo di base è `signed int` (tipo di C/C++).  
  
 btUInt  
 Tipo di base è `unsigned int` (tipo di C/C++).  
  
 btFloat  
 Tipo di base sono un numero a virgola mobile (`FLOAT`).  
  
 btBCD  
 Tipo di base è un numero decimale a livello di codice binario (`BCD`).  
  
 btBool  
 Tipo di base sono un valore booleano (`BOOL`).  
  
 btLong  
 Tipo di base è un `long int` (tipo di C/C++).  
  
 btULong  
 Tipo di base è un `unsigned long int` (tipo di C/C++).  
  
 btCurrency  
 Tipo di base sono di tipo valuta.  
  
 btDate  
 Tipo di base è data/ora (`DATE`).  
  
 btVariant  
 Tipo di base sono una struttura di tipo di variabile (`VARIANT`).  
  
 btComplex  
 Tipo di base è un numero complesso.  
  
 btBit  
 Tipo di base è un po'.  
  
 btBSTR  
 Tipo di base sono una stringa di base o binary (`BSTR`).  
  
 btHresult  
 Tipo di base è un `HRESULT`.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono restituiti per il [Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
