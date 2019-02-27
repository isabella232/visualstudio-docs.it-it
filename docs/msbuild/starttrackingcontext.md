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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c395df1e08f1b4e33e9cd34fec54bdd044f3b4c9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690513"
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
 **HRESULT** con il bit **SUCCEEDED** impostato se il contesto di rilevamento è stato creato.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *FileTracker.h*