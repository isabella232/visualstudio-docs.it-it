---
title: 'IDiaSymbol:: get_numberOfAcceleratorPointerTags | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b25cd941b8f06909ca1bf777d0e3251c78732706
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183184"
---
# <a name="idiasymbolget_numberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Restituisce il numero di tag del puntatore acceleratore in una funzione stub C++ AMP.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>Parametri  
 `count`  
 out Puntatore a un oggetto `DWORD` che include il numero di tag del puntatore dell'acceleratore in una funzione stub C++ amp.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo viene chiamato su un' `IDiaSymbol` interfaccia che corrisponde a una funzione dello stub di C++ amp Accelerator.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
