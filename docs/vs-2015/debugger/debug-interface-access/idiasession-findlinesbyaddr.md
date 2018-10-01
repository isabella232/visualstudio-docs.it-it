---
title: Findlinesbyaddr | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSession::findLinesByAddr method
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f070bc86691fff42abfd66055a96916f5f0878
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533182"
---
# <a name="idiasessionfindlinesbyaddr"></a>IDiaSession::findLinesByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Findlinesbyaddr](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findlinesbyaddr).  
  
Recupera le righe che contengono un indirizzo specificato in un modulo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findLinesByAddr (   
   DWORD                 seg,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `seg`  
 [in] Specifica il componente di sezione dell'indirizzo specifico.  
  
 `offset`  
 [in] Specifica il componente di offset di indirizzo specifico.  
  
 `length`  
 [in] Specifica il numero di byte dell'intervallo di indirizzi per coprire la query viene usata.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) oggetto che contiene un elenco di tutto la riga di numeri che coprono l'intervallo di indirizzi specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrata una funzione che ottiene tutti i numeri di riga inclusi in una funzione usando l'indirizzo e la lunghezza della funzione.  
  
```cpp#  
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,  
                                          IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                seg;  
    DWORD                offset;  
    ULONGLONG            length;  
  
    if (pFunc->get_addressSection ( &seg ) == S_OK &&  
        pFunc->get_addressOffset ( &offset ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)



