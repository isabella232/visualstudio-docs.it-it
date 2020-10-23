---
title: EndTrackingContext | Microsoft Docs
description: Informazioni su sintassi, valore restituito e requisiti per utilizzare MSBuild EndTrackingContext per terminare il contesto di rilevamento corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436672"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Consente di terminare il contesto di verifica corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Valore restituito

**HRESULT** con il bit **succeeded** impostato se il contesto di rilevamento è terminato.

## <a name="requirements"></a>Requisiti

**Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedere anche

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
