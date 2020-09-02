---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e791bc09ba3dd4f1811c650926eadb0f7f0462a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431641"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera i file di origine in base a modulo e Name.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCompiland`  
 in Oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il modulo da utilizzare come contesto per la ricerca. Impostare questo parametro su `NULL` per trovare i file di origine in tutti moduli.  
  
 `name`  
 in Specifica il nome del file di origine da recuperare. Impostare questo parametro su `NULL` per tutti i file di origine da recuperare.  
  
 `option`  
 in Specifica le opzioni di confronto applicate alla ricerca dei nomi. I valori dell'enumerazione [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) possono essere usati singolarmente o in combinazione.  
  
 `ppResult`  
 out Restituisce un oggetto [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) che contiene un elenco dei file di origine recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="example"></a>Esempio  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
