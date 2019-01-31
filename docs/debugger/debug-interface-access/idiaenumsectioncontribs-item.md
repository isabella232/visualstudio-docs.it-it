---
title: Idiaenumsectioncontribs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e14092c21497cc0126eb3eed169286418527c54
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069369"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Recupera i contributi di sezione per mezzo di un indice.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 indice  
 [in] Indice del [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetto da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` restituito dalle [Idiaenumsectioncontribs](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) (metodo).  
  
 section  
 [out] Restituisce un [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetto che rappresenta il contributo di sezione desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)