---
title: Idiaenumsectioncontribs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06a82fbb52ccdf0f9fb9fda50a74f2cfb30e7648
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190016"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera i contributi di sezione per mezzo di un indice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 index  
 [in] Indice del [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetto da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` restituito dalle [Idiaenumsectioncontribs](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) (metodo).  
  
 section  
 [out] Restituisce un [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetto che rappresenta il contributo di sezione desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
