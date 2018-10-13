---
title: Symbolbyid | Microsoft Docs
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
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60b7495abd70eb7e02408cfe711701ec15f5ac4b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272714"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un simbolo mediante il relativo identificatore univoco.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
```cpp#  
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



