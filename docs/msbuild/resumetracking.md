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
ms.openlocfilehash: 6bb4663013a73d88ed7c2118816007705834162c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578444"
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
 **Intestazione:** *FileTracker. h*

## <a name="see-also"></a>Vedere anche
- [SuspendTracking](../msbuild/suspendtracking.md)