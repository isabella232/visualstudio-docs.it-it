---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59d36847416801965841d79b5be9e9a654487b96
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986904"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Recupera i file di origine base compilando e al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCompiland`  
 [in] Un' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il modulo da utilizzare come contesto per la ricerca. Impostare questo parametro su `NULL` per trovare i file di origine in tutti i moduli.  
  
 `name`  
 [in] Specifica il nome del file di origine da recuperare. Impostare questo parametro su `NULL` per tutti i file di origine da recuperare.  
  
 `option`  
 [in] Specifica le opzioni di confronto applicate alla ricerca del nome. I valori di [enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumerazione può essere utilizzata singolarmente o in combinazione.  
  
 `ppResult`  
 [out] Restituisce un [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) recuperare l'oggetto che contiene un elenco dei file di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)