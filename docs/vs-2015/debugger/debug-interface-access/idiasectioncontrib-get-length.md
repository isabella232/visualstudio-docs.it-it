---
title: Get_length | Microsoft Docs
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
- IDiaSectionContrib::get_length method
ms.assetid: d0f6b9c7-90fc-4e3c-945a-b8f683a8f006
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79eb5226b9acc9f893b35b0d52ea370b6ceb7806
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892027"
---
# <a name="idiasectioncontribgetlength"></a>IDiaSectionContrib::get_length
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il numero di byte in una sezione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero di byte in una sezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



