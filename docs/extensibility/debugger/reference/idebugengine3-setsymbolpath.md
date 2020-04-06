---
title: IDebugEngine3::SetSymbolPath ??? Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730669"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Imposta il percorso o i percorsi cercati per i simboli di debug.

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
[in] Stringa contenente il percorso o i percorsi di ricerca dei simboli. Vedere "Osservazioni" per i dettagli. Non può essere null.

`szSymbolCachePath`\
[in] Stringa contenente il percorso locale in cui i simboli possono essere memorizzati nella cache. Non può essere null.

`Flags`\
[in] Non utilizzato; sempre impostato su 0.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 La `szSymbolSearchPath` stringa è un elenco di uno o più percorsi, separati da punto e virgola, per la ricerca di simboli. Questi percorsi possono essere un percorso locale, un percorso in stile UNC o un URL. Questi percorsi possono anche essere un mix di diversi tipi. Se il percorso è UNC \\(ad esempio, "Symserver" o "Symbols"), il motore di debug deve determinare se il percorso è `szSymbolCachePath`diretto a un server di simboli e deve essere in grado di caricare simboli da tale server, memorizzandoli nella cache nel percorso specificato da .

 Il percorso dei simboli può contenere anche uno o più percorsi della cache. Le cache sono elencate in ordine di priorità, con la cache con priorità più alta e separate da simboli . Ad esempio:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Il [metodo LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) esegue il caricamento effettivo dei simboli.

## <a name="see-also"></a>Vedere anche
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
