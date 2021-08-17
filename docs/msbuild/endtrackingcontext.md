---
title: EndTrackingContext | Microsoft Docs
description: Informazioni sulla sintassi, sul valore restituito e sui requisiti per usare MSBuild EndTrackingContext per terminare il contesto di rilevamento corrente.
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
ms.openlocfilehash: 4f4a0cd1b327f9be99b07e90bc7564a17ec13472
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054795"
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
