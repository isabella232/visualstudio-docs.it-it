---
title: Idiareadexeatoffsetcallback | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9f1c1ab49205a299b73837685b3d35b352a855d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837984"
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
  
 [dati]  
 [in, out] Matrice che viene compilata con byte letti dal file.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal codice di supporto di DIA per caricare i byte di dati da un eseguibile usando un offset di file assoluto. Questo metodo viene chiamato supportare le [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)