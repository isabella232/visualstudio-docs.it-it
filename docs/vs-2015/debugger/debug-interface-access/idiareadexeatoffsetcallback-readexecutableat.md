---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ac5452437ab6fdec3eb68baf46aeeab8434df4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538863"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 fileOffset  
 in Offset nel file eseguibile da cui iniziare la lettura.  
  
 cbData  
 in Numero di byte da leggere.  
  
 pcbData  
 out Restituisce il numero di byte letti.  
  
 data[]  
 [in, out] Matrice compilata con byte letti dal file.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo viene chiamato dal codice di supporto DIA per caricare i byte di dati da un eseguibile usando un offset assoluto del file. Questo metodo viene chiamato per supportare il metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
