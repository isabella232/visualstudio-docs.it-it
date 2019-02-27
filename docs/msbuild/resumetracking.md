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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e2ff32a4eb2218a8b3d09188c787156e484147f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596399"
---
# <a name="resumetracking"></a>ResumeTracking
Riprende la verifica nel contesto corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valore restituito
 **HRESULT** con il bit **SUCCEEDED** impostato se la verifica è ripresa. Se non è possibile riprendere la verifica perché il contesto non è disponibile viene restituito **E_FAIL**.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedere anche
- [SuspendTracking](../msbuild/suspendtracking.md)