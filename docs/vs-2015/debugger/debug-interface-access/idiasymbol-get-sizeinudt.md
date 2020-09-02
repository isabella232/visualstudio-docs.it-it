---
title: IDiaSymbol::get_sizeInUdt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: a82ab896-0185-46a4-b4d5-babfcc660fe1
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 147368e19bb1bcc1ccaa0bf94823df2e3f73a4be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428365"
---
# <a name="idiasymbolget_sizeinudt"></a>IDiaSymbol::get_sizeInUdt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la dimensione di un membro di un tipo definito dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_sizeInUdt(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Puntatore a un oggetto `DWORD` che specifica la dimensione del membro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
