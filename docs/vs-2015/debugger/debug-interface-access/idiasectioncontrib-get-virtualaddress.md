---
title: 'IDiaSectionContrib:: get_virtualAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_virtualAddress method
ms.assetid: e5b44a81-0804-429b-97d8-467cbba3132a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc4a92463f85941e4e8951e2cd7b6276bd727983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150522"
---
# <a name="idiasectioncontribget_virtualaddress"></a>IDiaSectionContrib::get_virtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera l'indirizzo virtuale (VA) del contributo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Restituisce il VA del contributo.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
