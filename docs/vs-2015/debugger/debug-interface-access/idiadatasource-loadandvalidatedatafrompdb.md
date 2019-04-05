---
title: IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f19a910af45ed70ae74c72441890ecae6c81d2a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954592"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
|Value|Descrizione|  
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
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
