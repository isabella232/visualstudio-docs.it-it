---
title: ResumeTracking | Microsoft Docs
description: Informazioni su sintassi, requisiti e valore restituito per MSBuild ResumeTracking, che riprende il rilevamento nel contesto corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6b2d7b4bd0bdbdf60864344edb552c884482a93e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143053"
---
# <a name="resumetracking"></a>ResumeTracking

Riprende la verifica nel contesto corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valore restituito

 HRESULT **con** il bit **SUCCEEDED** impostato se il rilevamento è stato ripreso. **E_FAIL** viene restituito se non è possibile riprendere il rilevamento perché il contesto non era disponibile.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [SuspendTracking](../msbuild/suspendtracking.md)