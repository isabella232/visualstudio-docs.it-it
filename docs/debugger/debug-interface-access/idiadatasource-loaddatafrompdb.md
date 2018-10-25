---
title: Loaddatafrompdb | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d1ed1d6edf2fc9ccc30f824cbfdf9ff67f0c2a5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918818"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Viene aperto e lo prepara un file di database (con estensione pdb) del programma come un'origine dati di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pdbPath  
 [in] Il percorso del file con estensione pdb.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Non è stato possibile aprire il file o determinato che il file di formato non è valido.|  
|E_PDB_FORMAT|È stato effettuato un tentativo di accedere a un file con formato obsoleto.|  
|E_INVALIDARG|Parametro non valido.|  
|E_UNEXPECTED|Origine dati è già stata preparata.|  
  
## <a name="remarks"></a>Note  
 Questo metodo carica i dati di debug direttamente da un file con estensione pdb.  
  
 Per convalidare il file con estensione PDB in base ai criteri specifici, usare il [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) (metodo).  
  
 Per ottenere l'accesso per il processo di caricamento dei dati (tramite un meccanismo di callback), usare il [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (metodo).  
  
 Per caricare un file con estensione pdb direttamente dalla memoria, usare il [Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) (metodo).  
  
## <a name="example"></a>Esempio  
  
```C++  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)