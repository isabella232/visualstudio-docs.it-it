---
title: IDiaSession::symbolById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba13c62f5e72e7192572def7b48046be3e1a20c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964458"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Recupera un simbolo mediante il relativo identificatore univoco.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 [in] Identificatore univoco.  
  
 `ppSymbol`  
 [out] Restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperare l'oggetto che rappresenta il simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'identificatore specificato è un valore univoco usato internamente dal DIA SDK per rendere univoco tutti i simboli.  
  
 Questo metodo può essere utilizzato, ad esempio, per recuperare il simbolo che rappresenta il tipo di simbolo di un altro (vedere l'esempio).  
  
## <a name="example"></a>Esempio  
 Questo esempio viene recuperata un' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il tipo di un altro simbolo. In questo esempio viene illustrato come utilizzare il `symbolById` metodo nella sessione. Un approccio più semplice consiste nel chiamare il [Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) metodo per recuperare direttamente il tipo di simbolo.  
  
```C++  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)