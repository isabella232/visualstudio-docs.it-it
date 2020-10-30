---
title: StopTrackingAndCleanup | Microsoft Docs
description: Informazioni su come MSBuild USA StopTrackingAndCleanup per arrestare tutti i tracciati e liberare la memoria usata dalla sessione di rilevamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05aec8bc85ac392670469da8073da02888b2f063
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048105"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Arresta tutte le operazioni di verifica e libera tutta la memoria usata dalla sessione di verifica.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Valore restituito

 Restituisce un **HRESULT** con il bit **succeeded** impostato se la verifica è stata arrestata.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [StartTrackingContext](../msbuild/starttrackingcontext.md)