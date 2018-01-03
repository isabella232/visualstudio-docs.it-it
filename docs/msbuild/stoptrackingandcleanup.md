---
title: StopTrackingAndCleanup | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StopTrackingAndCleanup
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c4ed935391ecdca464bc4b7e3b6e38342ad5afdc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Arresta tutte le operazioni di verifica e libera tutta la memoria usata dalla sessione di verifica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **HRESULT** con il bit **SUCCEEDED** impostato se la verifica è stata sospesa.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** FileTracker.h  
  
## <a name="see-also"></a>Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)