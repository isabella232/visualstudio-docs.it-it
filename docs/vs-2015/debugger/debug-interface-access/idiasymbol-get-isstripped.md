---
title: IDiaSymbol::get_isStripped | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStripped method
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 37fd166696d8fbcc913f26fb654ea5e709eb3a3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839703"
---
# <a name="idiasymbolget_isstripped"></a>IDiaSymbol::get_isStripped
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il flag che indica se i simboli privati sono stati rimossi dal file di simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_isStripped(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 out Restituisce `TRUE` se i simboli privati sono stati rimossi dal file di simboli; in caso contrario, restituisce `FALSE` .  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Commenti  
 Questa proprietà è disponibile dal `SymTagExe` tipo di simbolo (vedere [exe](../../debugger/debug-interface-access/exe.md)).  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|dia2. h|  
|Version:|DIA SDK v8.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)
