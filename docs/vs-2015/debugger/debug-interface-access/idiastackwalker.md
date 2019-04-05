---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6f5f5c3fa70c022175208cee492f3c0e752826e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954261"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fornisce metodi per eseguire uno stack viene descritto l'uso di informazioni nel file con estensione pdb.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaStackWalker`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumeratore di frame dello stack x86 a piattaforme.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumeratore di frame dello stack per un tipo di piattaforma specifica.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene utilizzata per ottenere un elenco di stack frame per un modulo caricato. Ogni metodo viene passata un' [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) oggetto (implementato dall'applicazione client) che fornisce le informazioni necessarie per creare l'elenco di stack frame.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta chiamando il `CoCreateInstance` metodo con l'identificatore di classe `CLSID_DiaStackWalker` e l'ID di interfaccia di `IID_IDiaStackWalker`. Nell'esempio viene illustrato come questa interfaccia è ottenuta.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come ottenere il `IDiaStackWalker` interfaccia.  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: DIA2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
