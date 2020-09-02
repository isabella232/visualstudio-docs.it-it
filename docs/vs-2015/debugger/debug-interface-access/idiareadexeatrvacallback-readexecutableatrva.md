---
title: 'IDiaReadExeAtRVACallback:: ReadExecutableAtRVA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d74543b7b57d188712c04bc43429357a5140c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187264"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legge il numero specificato di byte a partire dall'indirizzo RVA (relative Virtual Address) specificato dal file eseguibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `relativeVirtualAddress`  
 in RVA nel file eseguibile da cui iniziare la lettura.  
  
 `cbData`  
 in Numero di byte da leggere.  
  
 `pcbData`  
 out Restituisce il numero di byte letti.  
  
 `data[]`  
 [in, out] Matrice compilata con byte letti dal file.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo viene chiamato dal codice di supporto DIA per caricare i byte di dati da un file eseguibile usando un indirizzo virtuale relativo. Questo metodo viene chiamato per supportare il metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
