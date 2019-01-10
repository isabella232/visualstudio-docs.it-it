---
title: Get_container | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9b528806091bb0b84e8bd2d10b4594b4bf4d018
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935879"
---
# <a name="idiasymbolgetcontainer"></a>IDiaSymbol::get_container
Questa funzione recupera un puntatore a un simbolo che rappresenta il contenitore/padre di questo simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce un puntatore a un `IDiaSymbol` contenente informazioni sul contenitore di questo simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce S_FALSE o un codice di errore.  
  
> [!NOTE]
>  Un valore restituito S_FALSE significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Description|  
|-----------------|-----------------|  
|Intestazione:|Dia2.h|  
|Versione:|DIA SDK 8.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)