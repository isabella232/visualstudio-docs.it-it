---
title: SetThreadCount | Microsoft Docs
description: Informazioni su come MSBuild USA SetThreadCount per impostare il conteggio globale dei thread e assegnare tale conteggio al thread corrente.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 01bfdae1dcd11d7df042948308c424b7773b3bb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048320"
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