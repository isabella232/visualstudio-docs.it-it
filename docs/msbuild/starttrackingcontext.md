---
title: StartTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50f62704897d68b0e323b948b8f4ed7e96a10c9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632108"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Avvia un contesto di verifica.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametri

[in] `intermediateDirectory`

 Directory in cui archiviare il log di rilevamento.

[in] `taskName`

 Identifica il contesto di verifica. Questo nome viene usato per creare il nome del file di log.

## <a name="return-value"></a>Valore restituito

 **HRESULT** con il bit **succeeded** impostato se il contesto di rilevamento è stato creato.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*
