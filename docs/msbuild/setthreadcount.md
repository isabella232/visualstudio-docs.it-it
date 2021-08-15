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
ms.openlocfilehash: 1f8e3792015696f5424ffe9134a78b1b88f780e5622e2292382bc5b18ff80cad
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121257485"
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