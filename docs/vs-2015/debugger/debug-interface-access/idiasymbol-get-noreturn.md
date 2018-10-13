---
title: Get_noreturn | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_noReturn method
ms.assetid: 704c1cc0-5b84-4334-a02a-70f43aff39d5
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99f4a118dc23e858aedb6bdf3ffce359cc0036a7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222007"
---
# <a name="idiasymbolgetnoreturn"></a>IDiaSymbol::get_noReturn
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che specifica se la funzione è stata contrassegnata come senza risultati con il [noreturn](http://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_noReturn(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pFlag  
 [out] Restituisce `TRUE` se la funzione è stata dichiarata come senza risultati con il `noreturn` dell'attributo; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|DIA SDK 8.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [noreturn](http://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d)



