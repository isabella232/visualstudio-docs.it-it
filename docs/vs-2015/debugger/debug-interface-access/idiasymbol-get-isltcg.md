---
title: IDiaSymbol::get_isLTCG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d355a05ba2d805349a84a842a00b699d6c1ef272
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696288"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che specifica se il [modulo](../../debugger/debug-interface-access/compiland.md) è stato collegato con l'opzione del linker [/LTCG (generazione di codice in fase di collegamento)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2), che favorisce l'ottimizzazione dell'intero programma. Questa opzione si applica solo al codice gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pFlag  
 out Restituisce `TRUE` se l'oggetto `compiland` è collegato all'opzione del linker/LTCG. in caso contrario, restituisce `FALSE` .  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|dia2. h|  
|Version:|DIA SDK v8.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
