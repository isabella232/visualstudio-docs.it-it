---
title: IDiaSectionContrib::get_notPaged | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_notPaged method
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1899e59e6eb11b53757d28f9babc09739b1fdad3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151887"
---
# <a name="idiasectioncontribget_notpaged"></a>IDiaSectionContrib::get_notPaged
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che indica se non è possibile eseguire il paging della sezione alla memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_notPaged (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out, retval] Restituisce `TRUE` se non è possibile eseguire il paging della sezione; in caso contrario, restituisce `FALSE` .  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
