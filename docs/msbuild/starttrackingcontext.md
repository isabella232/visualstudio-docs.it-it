---
title: StartTrackingContext | Microsoft Docs
description: Informazioni sui parametri, i requisiti e il valore restituito per MSBuild StartTrackingContext, che avvia un contesto di rilevamento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: afd46ac5ed538f4773e35c7c727f1cf5fdbcc69a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625500"
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

 HRESULT **con** il bit **SUCCEEDED** impostato se è stato creato il contesto di rilevamento.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*
