---
title: IDiaSymbol::findChildrenEx | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0ee0ee9938ba2529afd7ea437c56761e1768e8cd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954972"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera gli elementi figlio del simbolo. I simboli locali che vengono restituiti includono informazioni sull'intervallo in tempo reale, se il programma viene compilato con l'ottimizzazione su.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findChildrenEx (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `symtag`  
 [in] Specifica i tag di simboli degli elementi figlio da recuperare, come definito nel [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Impostare su `SymTagNull` per tutti gli elementi figlio da recuperare.  
  
 `name`  
 [in] Specifica il nome degli elementi figlio da recuperare. Impostare su `NULL` per tutti gli elementi figlio da recuperare.  
  
 `compareFlags`  
 [in] Specifica le opzioni di confronto da applicare al corrispondenza dei nomi. I valori di [enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumerazione può essere utilizzata singolarmente o in combinazione.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recuperare l'oggetto che contiene un elenco dei simboli figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se almeno un figlio del simbolo è stato trovato, o restituisce `S_FALSE` se nessun elemento figlio sono stato trovato; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è la versione estesa del [Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: DIA2.h  
  
 Libreria: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
