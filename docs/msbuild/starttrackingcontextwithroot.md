---
title: StartTrackingContextWithRoot | Microsoft Docs
description: Informazioni su come usare MSBuild StartTrackingContextWithRoot per avviare un contesto di rilevamento usando un file di risposta che specifica un marcatore radice.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 62ecbb05d0fd129709345c23887aca1d9ed201be
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625499"
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

 HRESULT **con** il bit **SUCCEEDED** impostato se il contesto di rilevamento è stato creato.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [StartTrackingContext](../msbuild/starttrackingcontext.md)