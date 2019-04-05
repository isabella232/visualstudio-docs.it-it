---
title: IDiaSymbol::get_hasLongJump | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c949e9d04611bcce0d927d6d79cc06b8bdaac00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954389"
---
# <a name="idiasymbolgethaslongjump"></a>IDiaSymbol::get_hasLongJump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che specifica se la funzione contiene un utilizzo di [longjmp](http://msdn.microsoft.com/library/0e13670a-5130-45c1-ad69-6862505b7a2f) comando (associato a un [setjmp](http://msdn.microsoft.com/library/684a8b27-e8eb-455b-b4a8-733ca1cbd7d2) comando, che costituiscono il metodo di tipo C di gestione delle eccezioni).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_hasLongJump  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [out] Restituisce `TRUE` se la funzione contiene un `longjmp` comando; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Version:|DIA SDK v8.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)   
 [longjmp](http://msdn.microsoft.com/library/0e13670a-5130-45c1-ad69-6862505b7a2f)   
 [setjmp](http://msdn.microsoft.com/library/684a8b27-e8eb-455b-b4a8-733ca1cbd7d2)
