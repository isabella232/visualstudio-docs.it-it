---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68d585361b9797bf1df9c8b0b31f8a089e9de025
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632095"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Avvia un contesto di verifica usando un file di risposta che specifica un marcatore radice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametri

[in] `intermediateDirectory`

 Directory in cui archiviare il log di rilevamento.

[in] `taskName`

 Identifica il contesto di verifica. Questo nome viene usato per creare il nome del file di log.

[in] `rootMarkerResponseFile`

 Percorso di un file di risposta che contiene un marcatore radice. Il nome radice viene usato per raggruppare tutte le verifiche relative a un contesto.

## <a name="return-value"></a>Valore restituito

 **HRESULT** con il bit **SUCCEEDED** impostato se è stato creato il contesto di rilevamento.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedere anche

- [StartTrackingContext](../msbuild/starttrackingcontext.md)