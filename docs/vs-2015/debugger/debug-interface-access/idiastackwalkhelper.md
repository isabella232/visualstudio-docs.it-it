---
title: IDiaStackWalkHelper | Microsoft Docs
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
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8af7a0f463fc5d2089b374ac881cd0089dce0c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540707"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDiaStackWalkHelper](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper).  
  
Semplifica i percorsi nello stack usando il file di database (con estensione pdb) di debug programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine VTable  
 Nella tabella seguente sono illustrati i metodi di `IDiaStackWalkHelper`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Recupera il valore di un registro.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Imposta il valore di un registro.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Legge un blocco di dati dall'immagine del file eseguibile in memoria.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Cerca stack frame specificato per l'indirizzo del mittente (funzione) più vicino.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Cerca stack frame specificato per un indirizzo del mittente o in prossimità l'indirizzo specificato nello stack.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera lo stack frame contenente l'indirizzo virtuale specificato.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera il simbolo che contiene l'indirizzo virtuale specificato. **Nota:** simbolo deve avere il tipo `SymTagFunctionType` (un valore compreso il [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Restituisce il blocco di dati PDATA associato all'indirizzo virtuale specificato.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Recupera l'indirizzo virtuale iniziale di un file eseguibile, dato un indirizzo virtuale in una posizione nello spazio di memoria dell'eseguibile.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene chiamata dal codice DIA per ottenere informazioni sull'eseguibile per costruire un elenco di frame dello stack durante l'esecuzione del programma.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un'applicazione client implementa questa interfaccia per supportare i percorsi nello stack durante l'esecuzione del programma. Un'istanza di questa interfaccia viene passata per la [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) oppure [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) metodi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)



