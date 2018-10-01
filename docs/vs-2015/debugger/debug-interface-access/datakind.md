---
title: DataKind | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25d560012ae51a039572cfc3bd7a53e10fb1175d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526973"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [DataKind](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/datakind).  
  
Indica l'ambito specifico di un valore di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum DataKind {   
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
 Non è possibile determinare il simbolo dei dati.  
  
 DataIsLocal  
 Elemento dati è una variabile locale.  
  
 DataIsStaticLocal  
 Elemento dati è una variabile locale statica.  
  
 DataIsParam  
 Elemento dati è un parametro formale.  
  
 DataIsObjectPtr  
 Elemento dati è un puntatore a oggetto (`this`).  
  
 DataIsFileStatic  
 Elemento di dati è una variabile con ambito file.  
  
 DataIsGlobal  
 Elemento dati è una variabile globale.  
  
 DataIsMember  
 Elemento dati è una variabile membro oggetto.  
  
 DataIsStaticMember  
 Elemento dati è una variabile di classe statici.  
  
 DataIsConstant  
 Elemento dati è un valore costante.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono restituiti per il [Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)



