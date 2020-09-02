---
title: IDiaLineNumber::get_columnNumberEnd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d6fb8cb5b3cfa7aa741db4e49dc7c2b3e1daee4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192344"
---
# <a name="idialinenumberget_columnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il numero della colonna di origine in base 1 in cui termina l'espressione o l'istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Restituisce il numero di colonna in cui termina l'espressione o l'istruzione. Se il valore è zero, le informazioni sull'estremità della colonna non sono presenti.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore della colonna restituito da questo metodo è un offset di byte nella riga alla posizione dopo l'ultimo carattere dell'istruzione sulla riga.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
