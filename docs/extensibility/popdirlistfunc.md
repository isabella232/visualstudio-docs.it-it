---
title: POPDIRLISTFUNC | Microsoft Docs
description: Informazioni sulla funzione di callback POPDIRLISTFUNC, che viene passata alle directory di aggiornamento per scoprire quali sono inclusi nel controllo del codice sorgente.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 805d7a5c9250bc511692c497bc9083852dad2301
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863444"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Si tratta di una funzione di callback assegnata alla funzione [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) per aggiornare una raccolta di directory e (facoltativamente) i nomi di file per scoprire quali sono inclusi nel controllo del codice sorgente.

 Il `POPDIRLISTFUNC` callback deve essere chiamato solo per le directory e i nomi file (nell'elenco fornito alla `SccPopulateDirList` funzione) che sono effettivamente sotto il controllo del codice sorgente.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData

in Valore utente assegnato a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` Se il nome in `lpDirectoryOrFileName` è una directory; in caso contrario, il nome è un nome file.

 lpDirectoryOrFileName

in Percorso locale completo di una directory o di un nome file nel controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'IDE restituisce un codice di errore appropriato:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Continuare l'elaborazione.|
|SCC_I_OPERATIONCANCELED|Consente di arrestare l'elaborazione.|
|SCC_E_xxx|Qualsiasi errore appropriato del controllo del codice sorgente dovrebbe arrestare l'elaborazione.|

## <a name="remarks"></a>Commenti
 Se il `fOptions` parametro della `SccPopulateDirList` funzione contiene il `SCC_PDL_INCLUDEFILES` flag, l'elenco conterrà anche nomi di file e nomi di directory.

## <a name="see-also"></a>Vedi anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Codici di errore](../extensibility/error-codes.md)
