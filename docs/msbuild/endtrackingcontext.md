---
title: EndTrackingContext | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60db5058f3a084a4d24f3b3a1d83e615a9071d8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920254"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
Consente di terminare il contesto di verifica corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Valore restituito  
 **HRESULT** con il bit **SUCCEEDED** impostato se il contesto di verifica è terminato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *FileTracker.h*  
  
## <a name="see-also"></a>Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)