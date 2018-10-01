---
title: Get_frontendminor | Microsoft Docs
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
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19b9afac7c724df04b565d947f7168cb780a2bc4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517177"
---
# <a name="idiasymbolgetfrontendminor"></a>IDiaSymbol::get_frontEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Get_frontendminor](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-frontendminor).  
  
Recupera il numero di versione secondaria del front-end.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero di versione secondaria front.end.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Un compilatore è in genere costituito da due elementi principali: il front-end (parser), che gestisce l'analisi del codice sorgente in un modulo intermedio, e un back-end (Generatore di codice), che converte il formato intermedio in assembly. Non è insolito per il front-end avere una versione diversa rispetto al back-end.  
  
 Un front-end o un numero di versione back-end è costituito da tre parti: \<principale >.\< secondaria >. \<compilazione >, dove \<principali > è il numero di versione principale, \<secondaria > è il numero di versione secondaria, e \<compilazione > è il numero di build. Ad esempio, 13.10.3077.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



