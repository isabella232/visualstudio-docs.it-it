---
title: SuspendTracking | Microsoft Docs
description: Informazioni sulla sintassi, i requisiti e il valore restituito per MSBuild SuspendTracking, che sospende il rilevamento nel contesto corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048095"
---
# <a name="suspendtracking"></a>SuspendTracking

Sospende la verifica nel contesto corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Valore restituito

 **HRESULT** con il bit **succeeded** impostato se la verifica è stata sospesa.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [ResumeTracking](../msbuild/resumetracking.md)