---
title: IDiaSymbol::get_numberOfRegisterIndices | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1ec8b8ea-e423-4327-8dc0-a390e6e3ffb0
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18506739ca113679590b63a3a6bec981374da144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183152"
---
# <a name="idiasymbolget_numberofregisterindices"></a>IDiaSymbol::get_numberOfRegisterIndices
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il numero di indici di registro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_numberOfRegisterIndices(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Puntatore a un oggetto `DWORD` che include il numero di indici di registro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
