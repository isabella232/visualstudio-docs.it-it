---
title: Proprietà POPDIRLISTFUNC . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702076"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Si tratta di una funzione di callback assegnata alla funzione [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) per aggiornare una raccolta di directory e (facoltativamente) i nomi di file per scoprire quali sono nel controllo del codice sorgente.

 Il `POPDIRLISTFUNC` callback deve essere chiamato solo per le directory e `SccPopulateDirList` i nomi di file (nell'elenco assegnato alla funzione) che sono effettivamente sotto il controllo del codice sorgente.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData (informazioni in fibra con i dati)

[in] Valore utente assegnato a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bCartella

[in] `TRUE` se il `lpDirectoryOrFileName` nome in è una directory; in caso contrario, il nome è un nome di file.

 LpDirectoryOrNomeFileName

[in] Percorso locale completo di una directory o di un nome di file in cui si trova il controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'IDE restituisce un codice di errore appropriato:The IDE returns an appropriate error code:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Continuare l'elaborazione.|
|SCC_I_OPERATIONCANCELED|Consente di arrestare l'elaborazione.|
|SCC_E_xxx|Qualsiasi errore di controllo del codice sorgente appropriato deve interrompere l'elaborazione.|

## <a name="remarks"></a>Osservazioni
 Se `fOptions` il parametro `SccPopulateDirList` della `SCC_PDL_INCLUDEFILES` funzione contiene il flag, l'elenco conterrà probabilmente nomi di file e nomi di directory.

## <a name="see-also"></a>Vedere anche
- [Callback functions implemented by the IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Codici di errore](../extensibility/error-codes.md)
