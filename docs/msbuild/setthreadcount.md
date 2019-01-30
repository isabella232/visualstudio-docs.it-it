---
title: SetThreadCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b4bfb8e1f60ed668039011841e12021e0f0702f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942009"
---
# <a name="setthreadcount"></a>SetThreadCount
Imposta il conteggio dei thread globale e assegna tale conteggio al thread corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cmd  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parametri  
 [in] `threadCount`  
 Numero di thread da usare.  
  
## <a name="return-value"></a>Valore restituito  
 **HRESULT** con il bit **SUCCEEDED** impostato se il conteggio thread è stato aggiornato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *FileTracker.h*