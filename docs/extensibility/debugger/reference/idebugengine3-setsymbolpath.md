---
description: Imposta il percorso o i percorsi in cui vengono cercati i simboli di debug.
title: 'IDebugEngine3:: SetSymbolPath | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e2b029413e3b402e1d8dfa19ccb3ad22644b241
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153690"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Imposta il percorso o i percorsi in cui vengono cercati i simboli di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>Parametri

`szSymbolSearchPath`\
in Stringa che contiene il percorso o i percorsi di ricerca dei simboli. Per informazioni dettagliate, vedere la sezione "osservazioni". Non può essere null.

`szSymbolCachePath`\
in Stringa contenente il percorso locale in cui i simboli possono essere memorizzati nella cache. Non può essere null.

`Flags`\
in Non utilizzato; sempre impostato su 0.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 La stringa `szSymbolSearchPath` è un elenco di uno o più percorsi, separati da punti e virgola, per la ricerca di simboli. Questi percorsi possono essere un percorso locale, un percorso di tipo UNC o un URL. Questi percorsi possono anche essere costituiti da una combinazione di tipi diversi. Se il percorso è UNC (ad esempio, \\ \Symserver\Symbols), il motore di debug deve determinare se il percorso è un server di simboli e deve essere in grado di caricare i simboli da tale server, inserendoli nella cache nel percorso specificato da `szSymbolCachePath` .

 Il percorso dei simboli può anche contenere uno o più percorsi della cache. Le cache sono elencate in ordine di priorità, con la prima cache con priorità più elevata e separate da * simboli. Ad esempio:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Il metodo [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) esegue il carico effettivo dei simboli.

## <a name="see-also"></a>Vedi anche
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
