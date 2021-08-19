---
description: Fornisce metodi per eseguire una procedura di analisi dello stack usando le informazioni contenute nel file con estensione pdb.
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c27a18923ae5b305702994e4d76be7dd291eb8c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113563"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Fornisce metodi per eseguire una procedura di analisi dello stack usando le informazioni contenute nel file con estensione pdb.

## <a name="syntax"></a>Sintassi

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDiaStackWalker` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumeratore stack frame per piattaforme x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumeratore stack frame per un tipo di piattaforma specifico.|

## <a name="remarks"></a>Commenti
Questa interfaccia viene usata per ottenere un elenco di stack frame per un modulo caricato. A ognuno dei metodi viene passato un oggetto [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (implementato dall'applicazione client) che fornisce le informazioni necessarie per creare l'elenco di stack frame.

## <a name="notes-for-callers"></a>Note per i chiamanti
Questa interfaccia viene ottenuta chiamando il `CoCreateInstance` metodo con l'identificatore di classe `CLSID_DiaStackWalker` e l'ID di interfaccia di `IID_IDiaStackWalker` . L'esempio mostra come viene ottenuta questa interfaccia.

## <a name="example"></a>Esempio
In questo esempio viene illustrato come ottenere `IDiaStackWalker` l'interfaccia .

```C++

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
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
