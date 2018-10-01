---
title: Loadandvalidatedatafrompdb | Microsoft Docs
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
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e4b425406f6f6b044226b791950f7d93acc95aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529683"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Loadandvalidatedatafrompdb](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb).  
  
Consente di aprire e verifica che il file di programma (PDB) del database corrisponda le informazioni sulla firma fornite e prepara il file con estensione PDB come un'origine dati di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdbPath`  
 [in] Il percorso del file con estensione pdb.  
  
 `pcsig70`  
 [in] Firma GUID per la verifica della firma di file con estensione pdb. File con solo con estensione PDB [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] e versioni successive dispongono di firme di GUID.  
  
 `sig`  
 [in] La firma di 32 bit per la verifica della firma di file con estensione pdb.  
  
 `age`  
 [in] Valore Age da verificare. Il periodo di validità non corrisponde necessariamente su qualsiasi valore di tempo noto, viene usato per determinare se un file con estensione PDB non è sincronizzato con un file .exe corrispondente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Non è stato possibile aprire il file o il file di formato non è valido.|  
|E_PDB_FORMAT|È stato effettuato un tentativo di accedere a un file con formato obsoleto.|  
|E_PDB_INVALID_SIG|Firma non corrisponde.|  
|E_PDB_INVALID_AGE|Non corrisponde a età.|  
|E_INVALIDARG|Parametro non valido.|  
|E_UNEXPECTED|L'origine dati è già stata preparata.|  
  
## <a name="remarks"></a>Note  
 Un file con estensione PDB contiene i valori di firma sia age. Questi valori vengono replicati nel file con estensione dll o .exe che corrisponde al file con estensione pdb. Prima di preparare l'origine dati, questo metodo verifica che age e la firma del file con estensione pdb denominato corrispondano ai valori forniti.  
  
 Per caricare un file con estensione pdb senza convalida, usare il [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) (metodo).  
  
 Per ottenere l'accesso per il processo di caricamento dei dati (tramite un meccanismo di callback), usare il [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (metodo).  
  
 Per caricare un file con estensione pdb direttamente dalla memoria, usare il [Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) (metodo).  
  
## <a name="example"></a>Esempio  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)



