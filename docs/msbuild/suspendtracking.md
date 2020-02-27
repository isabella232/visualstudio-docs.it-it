---
title: SuspendTracking | Microsoft Docs
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
ms.openlocfilehash: 950c6a07a46f7f4b970912e576257a577021367e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632010"
---
# <a name="suspendtracking"></a>SuspendTracking

Sospende la verifica nel contesto corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Valore restituito

 **HRESULT** con il bit **SUCCEEDED** impostato se la verifica è stata sospesa.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker. h*

## <a name="see-also"></a>Vedere anche

- [ResumeTracking](../msbuild/resumetracking.md)