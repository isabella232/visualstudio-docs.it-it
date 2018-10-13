---
title: IDiaSession::findInlineesByName | Microsoft Docs
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
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 534210b8f04fa10fd6193736860a2e31971d095a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227123"
---
# <a name="idiasessionfindinlineesbyname"></a>IDiaSession::findInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni sul numeri di riga di tutte le funzioni rese inline che corrisponde al nome specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findInlineesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `name`  
 [in] Specifica il nome da utilizzare per il confronto.  
  
 `option`  
 [in] Specifica le opzioni di confronto applicate alla ricerca del nome. I valori di [enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumerazione può essere utilizzata singolarmente o in combinazione.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) oggetto che contiene un elenco di numeri di riga che sono stati recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)



