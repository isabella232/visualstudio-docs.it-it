---
title: IDiaSymbol::get_udtKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fb58bec19460a78839ded86c9b7d194e838cb09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839787"
---
# <a name="idiasymbolget_udtkind"></a>IDiaSymbol::get_udtKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la varietà di un tipo definito dall'utente (UDT).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_udtKind (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Restituisce un valore dall'enumerazione Enumerazione [UdtKind](../../debugger/debug-interface-access/udtkind.md) che specifica il tipo di un tipo definito dall'utente: struttura, classe o Unione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o codice di errore.  
  
> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione UdtKind](../../debugger/debug-interface-access/udtkind.md)
