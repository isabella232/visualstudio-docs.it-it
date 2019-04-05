---
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7e24257402ddb546df63753bed62add2d33c512
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955707"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Consente a un'applicazione client fornire i byte di un file eseguibile come specificato dalla posizione del file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaReadExeAtOffsetCallback`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.|  
  
## <a name="remarks"></a>Note  
 L'applicazione client implementa questa interfaccia per fornire i byte del file eseguibile con un offset assoluto nel file dell'eseguibile. Per usare un indirizzo virtuale relativo, implementare il [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questo metodo è implementato dall'applicazione client e passato per la [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo come metodo alternativo per la lettura del file.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: DIA2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
