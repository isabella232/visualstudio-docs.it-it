---
title: Findlinesbyrva | Microsoft Docs
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
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d792389f816b5a9476419c992649c64d13a5f891
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173953"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera le righe che contengono un indirizzo virtuale relativo specificato (RVA) in un modulo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findLinesByRVA (   
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `rva`  
 [in] Specifica l'indirizzo come un RVA.  
  
 `length`  
 [in] Specifica il numero di byte dell'intervallo di indirizzi per coprire la query viene usata.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) oggetto che contiene un elenco di tutto la riga di numeri che coprono l'intervallo di indirizzi specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrata una funzione che ottiene tutti i numeri di riga contenuti nella funzione specificata usando l'indirizzo virtuale relativo della funzione e la lunghezza.  
  
```cpp#  
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                rva;  
    ULONGLONG            length;  
  
    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



