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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9af7c90342638fb0c154e7de21fa111d560905d0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048429"
---
# <a name="resumetracking"></a>ResumeTracking

Riprende la verifica nel contesto corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valore restituito

 **HRESULT** con il bit **succeeded** impostato se il rilevamento è stato ripreso. Viene restituito **E_FAIL** se non è possibile riprendere il rilevamento perché il contesto non è disponibile.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [SuspendTracking](../msbuild/suspendtracking.md)