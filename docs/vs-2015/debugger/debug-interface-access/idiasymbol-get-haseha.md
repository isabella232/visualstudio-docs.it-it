---
title: Get_haseha | Microsoft Docs
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
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a0e9bdc820483a1c4af7389c0af5bce4750163a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220493"
---
# <a name="idiasymbolgethaseha"></a>IDiaSymbol::get_hasEHa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che specifica se la funzione contiene gestione delle eccezioni asincrone (strutturate).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_hasEHa(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [out] Restituisce `TRUE` se la funzione ha la gestione delle eccezioni asincrone; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 È possibile combinare asincrona o non strutturate gestione delle eccezioni con la gestione delle eccezioni di tipo C++, ma necessaria un'opzione del compilatore specifici, /EHa, per abilitarlo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|DIA SDK 8.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



