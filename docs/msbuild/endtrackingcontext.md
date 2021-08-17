---
title: EndTrackingContext | Microsoft Docs
description: Informazioni sulla sintassi, sul valore restituito e sui requisiti da usare MSBuild EndTrackingContext per terminare il contesto di rilevamento corrente.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: debfb2a287c8efe447c0c1fa299ddf15d25936f802609c4b00a55dfb91a646f6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397930"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Consente di terminare il contesto di verifica corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Valore restituito

HRESULT **con** il bit **SUCCEEDED** impostato se il contesto di rilevamento è stato terminato.

## <a name="requirements"></a>Requisiti

**Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
