---
title: IDiaSession::findSymbolByVAEx | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVAEx method
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14a0b573609d52269809dcaa6e900e17affcecfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196369"
---
# <a name="idiasessionfindsymbolbyvaex"></a>IDiaSession::findSymbolByVAEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo virtuale (VA) e un offset specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findSymbolByVAEx (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `va`  
 in Specifica il VA.  
  
 `symtag`  
 in Tipo di simbolo da trovare. I valori vengono ricavati dall'enumerazione [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 out Restituisce un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il simbolo recuperato.  
  
 `displacement`  
 out Restituisce un valore che specifica un offset dall'indirizzo virtuale fornito da `va` .  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="example"></a>Esempio  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession:: findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
