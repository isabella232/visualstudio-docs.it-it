---
title: Get_isdataaligned | Microsoft Docs
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
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e01ab9de41bd8ead1348eb58308008e55e6323e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891974"
---
# <a name="idiasymbolgetisdataaligned"></a>IDiaSymbol::get_isDataAligned
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che specifica se il tipo definito dall'utente (UDT) è stato allineato per alcuni limiti di memoria specifica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_isDataAligned(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [out] Restituisce `TRUE` se il tipo definito dall'utente è stato allineato a un limite di memoria; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Questa proprietà è impostata in genere quando il file eseguibile viene compilato con l'allineamento dei dati non predefinite. Ad esempio, il compilatore Microsoft C++ può modificare l'allineamento di dati con l'opzione della riga di comando, /Zp<em>#</em>, dove *#* è un valore di byte.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|DIA SDK 8.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



