---
title: IDiaSectionContrib::get_length | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_length method
ms.assetid: d0f6b9c7-90fc-4e3c-945a-b8f683a8f006
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8ff6b4d35447125d5923bea1a0b2d2bb48dff79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421616"
---
# <a name="idiasectioncontribget_length"></a>IDiaSectionContrib::get_length
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
 out Restituisce il numero di byte in una sezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
