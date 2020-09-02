---
title: DataKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197630"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica l'ambito specifico di un valore di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elementi  
 DataIsUnknown  
 Non è possibile determinare il simbolo di dati.  
  
 DataIsLocal  
 L'elemento dati è una variabile locale.  
  
 DataIsStaticLocal  
 L'elemento dati è una variabile locale statica.  
  
 DataIsParam  
 L'elemento dati è un parametro formale.  
  
 DataIsObjectPtr  
 L'elemento dati è un puntatore a oggetto ( `this` ).  
  
 DataIsFileStatic  
 L'elemento dati è una variabile con ambito file.  
  
 DataIsGlobal  
 L'elemento dati è una variabile globale.  
  
 DataIsMember  
 L'elemento dati è una variabile membro oggetto.  
  
 DataIsStaticMember  
 L'elemento dati è una variabile statica di classe.  
  
 DataIsConstant  
 L'elemento dati è un valore costante.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di questa enumerazione vengono restituiti dal metodo [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst. h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
