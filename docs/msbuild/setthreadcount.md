---
title: SetThreadCount | Microsoft Docs
description: Informazioni su MSBuild setThreadCount per impostare il conteggio globale dei thread e assegnare tale conteggio al thread corrente.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 35649f2ae7c0aec8b713573fc5b9f8f29e86ac2f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625553"
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

 HRESULT **con** il bit **SUCCEEDED** impostato se il conteggio dei thread è stato aggiornato.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*