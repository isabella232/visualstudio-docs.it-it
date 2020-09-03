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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 102f46ec639719bb2bec70a38c6c7177c63793c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632329"
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

 **HRESULT** con il bit **succeeded** impostato se il conteggio dei thread è stato aggiornato.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*