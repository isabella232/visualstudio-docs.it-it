---
title: IDiaSymbol::get_optimizedCodeDebugInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_optimizedCodeDebugInfo method
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 32279f4539e52335c4999c07e10053c70ad3860f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840262"
---
# <a name="idiasymbolget_optimizedcodedebuginfo"></a>IDiaSymbol::get_optimizedCodeDebugInfo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che indica se la funzione contiene informazioni di debug specifiche per il codice ottimizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_optimizedCodeDebugInfo(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 out Restituisce `TRUE` se la funzione o l'etichetta ottimizzata contiene informazioni di debug; in caso contrario, restituisce `FALSE` .  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|dia2. h|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
