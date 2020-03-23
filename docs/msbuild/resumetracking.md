---
title: ResumeTracking | Microsoft Docs
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
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632498"
---
# <a name="resumetracking"></a>ResumeTracking

Riprende la verifica nel contesto corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valore restituito

 **HRESULT** con il bit **SUCCEEDED** impostato se il rilevamento è stato ripreso. **E_FAIL** viene restituito se non è possibile riprendere il rilevamento perché il contesto non era disponibile.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedere anche

- [SuspendTracking](../msbuild/suspendtracking.md)