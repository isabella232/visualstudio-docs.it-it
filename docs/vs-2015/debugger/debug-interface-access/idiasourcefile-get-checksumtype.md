---
title: IDiaSourceFile::get_checksumType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f859bce63e2976b23ab613e249dad41b2bc63486
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967623"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il tipo di checksum.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il tipo di checksum.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il tipo di checksum è un valore che può essere mappato a un algoritmo di checksum. Ad esempio, il formato di file PDB standard in genere può avere uno dei valori seguenti:  
  
|Tipo di checksum|Etichetta CryptoAPI|Descrizione|  
|-------------------|---------------------|-----------------|  
|0|\<nessuno>|Checksum non presente.|  
|1|`CALG_MD5`|checksum generato con l'algoritmo hash MD5.|  
|2|`CALG_SHA1`|checksum generato con l'algoritmo di hash SHA1.|  
  
 Il `CryptoAPI` le etichette sono compresi il `ALG_ID` enumerazione. Per altre informazioni su algoritmi di hash, consultare il `CryptoAPI` sezione di Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)].  
  
 Per ottenere i byte di valore di checksum effettivo per il file di origine, chiamare il [Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
