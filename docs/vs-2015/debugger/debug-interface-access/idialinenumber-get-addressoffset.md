---
title: Idialinenumber | Microsoft Docs
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
- IDiaLineNumber::get_addressOffset method
ms.assetid: 3bcb5500-b26c-4d3c-9d81-0a389a3715c3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d454d81aaab15a9e095e7f7ef4d83c2fe0a0981f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938344"
---
# <a name="idialinenumbergetaddressoffset"></a>IDiaLineNumber::get_addressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la parte offset di indirizzo di memoria in cui inizia un blocco.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce la parte offset di indirizzo di memoria in cui inizia un blocco.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="example"></a>Esempio  
  
```cpp#  
CComPtr< IDiaLineNumber > pLine;  
DWORD offset;  
pLine->get_addressOffset( &offset);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)



