---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3a637608c8da5d7c5c5e0d857520a08ffae494a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944866"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 fileOffset  
 [in] Offset nel file eseguibile per iniziare la lettura.  
  
 cbData  
 [in] Numero di byte da leggere.  
  
 pcbData  
 [out] Restituisce il numero di byte letti.  
  
 data[]  
 [in, out] Matrice che viene compilata con byte letti dal file.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal codice di supporto di DIA per caricare i byte di dati da un eseguibile usando un offset di file assoluto. Questo metodo viene chiamato supportare le [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)