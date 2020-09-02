---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8275756a4b89ab56148a9f7b560eda5d671fc6a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150587"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Consente a un'applicazione client di fornire byte di un file eseguibile come specificato da un indirizzo virtuale relativo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDiaReadExeAtRVACallback` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Legge il numero specificato di byte a partire dall'indirizzo RVA (relative Virtual Address) specificato dal file eseguibile.|  
  
## <a name="remarks"></a>Osservazioni  
 L'applicazione client implementa questa interfaccia per fornire i byte del file eseguibile usando un indirizzo virtuale relativo nel file dell'eseguibile. Per usare un offset assoluto dei file, implementare l'interfaccia [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questo metodo viene implementato dall'applicazione client e passato al metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) come metodo alternativo per la lettura del file.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dia2. h  
  
 Libreria: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
