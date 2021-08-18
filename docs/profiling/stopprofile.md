---
title: StopProfile | Microsoft Docs
description: Informazioni sulla funzione StopProfile e su come imposta il contatore su 0 (off) per il livello di profilatura specificato.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4887f5a86f63d4ee68e560b16bcd675959c9c85e1d6557186262e3b946ee8db9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121354004"
---
# <a name="stopprofile"></a>StopProfile
La funzione `StopProfile` imposta il contatore su 0 (OFF) per il livello di profilatura specificato.

## <a name="syntax"></a>Sintassi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parametri
 `Level`

 Indica il livello di profilatura a cui può essere applicata la raccolta di dati sulle prestazioni. Gli enumeratori **PROFILE_CONTROL_LEVEL** seguenti possono essere usati per indicare uno dei tre livelli a cui può essere applicata la raccolta di dati sulle prestazioni:

|Enumeratore|Descrizione|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Impostazione del livello globale con effetti su tutti i processi e i thread nell'esecuzione della profilatura.|
|PROFILE_PROCESSLEVEL|Impostazione del livello processo con effetti su tutti i thread che fanno parte del processo specificato.|
|PROFILE_THREADLEVEL|Impostazione del livello thread con effetti sul thread specificato.|

 `dwId`

 Identificatore del processo o del thread generato dal sistema.

## <a name="property-valuereturn-value"></a>Valore proprietà/valore restituito
 La funzione indica esito l'esito positivo o negativo tramite l'enumerazione **PROFILE_COMMAND_STATUS**. Il valore restituito può essere uno dei seguenti:

|Enumeratore|Descrizione|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|L'ID dell'elemento di profilatura non esiste.|
|PROFILE_ERROR_LEVEL_NOEXIST|Il livello di profilatura specificato non esiste.|
|PROFILE_ERROR_MODE_NEVER|La modalità di profilatura è stata impostata su NEVER al momento della chiamata della funzione.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|La chiamata della funzione di profilatura, il livello di profilatura o la combinazione di chiamata e livello non sono ancora stati implementati.|
|PROFILE_OK|La chiamata è stata completata correttamente.|

## <a name="remarks"></a>Commenti
 StartProfile e StopProfile controllano lo stato di Start/Stop per il livello di profilatura. Il valore predefinito di Start/Stop è 1. Il valore iniziale può essere modificato nel Registro di sistema. Ogni chiamata a StartProfile imposta Start/Stop su 1. Ogni chiamata a StopProfile lo imposta su 0.

 Quando Start/Stop è maggiore di 0, lo stato di Start/Stop per il livello è impostato su ON. Quando è minore o uguale a 0, lo stato di Start/Stop è OFF.

 Se lo stato di Start/Stop e lo stato di Suspend/Resume sono entrambi ON, lo stato di profilatura per il livello è ON. Affinché un thread venga incluso nella profilatura, gli stati dei livelli globale, processo e thread per il thread devono essere ON.

## <a name="net-framework-equivalent"></a>Equivalente .NET Framework
 Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Informazioni sulla funzione
 Intestazione: dichiarata in VSPerf.h

 Libreria di importazione: VSPerf.lib

## <a name="example"></a>Esempio
 L'esempio seguente illustra il metodo StopProfile. Nell'esempio si presuppone che sia stata effettuata una chiamata al metodo StartProfile per lo stesso thread o processo identificato da [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
void ExerciseStopProfile()
{
    // StartProfile and StopProfile control the
    // Start/Stop state for the profiling level.
    // The default initial value of Start/Stop is 1.
    // The initial value can be changed in the registry.
    // Each call to StartProfile sets Start/Stop to 1;
    // each call to StopProfile sets it to 0.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to StopProfile.
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = StopProfile(
        PROFILE_THREADLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("StopProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Vedi anche
- [Visual Studio riferimento all'API del profiler (nativo)](../profiling/visual-studio-profiler-api-reference-native.md)
