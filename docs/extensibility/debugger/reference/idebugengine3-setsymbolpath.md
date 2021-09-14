---
description: Imposta il percorso o i percorsi in cui vengono cercati i simboli di debug.
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73e7d4cb8ed36546e60326bc0935817d9b647adb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710307"
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
[in] Stringa contenente il percorso o i percorsi di ricerca dei simboli. Per informazioni dettagliate, vedere "Osservazioni". Non può essere null.

`szSymbolCachePath`\
[in] Stringa contenente il percorso locale in cui è possibile memorizzare i simboli nella cache. Non può essere null.

`Flags`\
[in] Non usato; è sempre impostato su 0.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 La stringa è un elenco di uno o più percorsi, separati da punti `szSymbolSearchPath` e virgola, per cercare i simboli. Questi percorsi possono essere un percorso locale, un percorso di tipo UNC o un URL. Questi percorsi possono anche essere una combinazione di tipi diversi. Se il percorso è UNC (ad esempio, \\ \Symserver\Symbols), il motore di debug deve determinare se il percorso è a un server di simboli e deve essere in grado di caricare i simboli da tale server, memorizzandoli nella cache nel percorso specificato da `szSymbolCachePath` .

 Il percorso del simbolo può contenere anche uno o più percorsi della cache. Le cache sono elencate in ordine di priorità, con prima la cache con la priorità più alta e separate da simboli *. Ad esempio:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Il [metodo LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) esegue il carico effettivo dei simboli.

## <a name="see-also"></a>Vedi anche
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
