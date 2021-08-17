---
title: SuspendProfile | Microsoft Docs
description: Informazioni su come il metodo SuspendProfile incrementa il contatore Suspend/Resume per il livello di profilatura specificato.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 05b3ed78dc22a713c5d567e9b29f8616ceee63c2366e170d008d6e7d0a9716f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441696"
---
# <a name="suspendprofile"></a>SuspendProfile
Il metodo `SuspendProfile` incrementa il contatore Suspend/Resume per il livello di profilatura specificato.

## <a name="syntax"></a>Sintassi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(
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
 Il valore iniziale del contatore Suspend/Resume è 0. Ogni chiamata a SuspendProfile aggiunge 1 al conteggio di Suspend/Resume. Ogni chiamata a ResumeProfile sottrae 1.

 Quando il conteggio di Suspend/Resume è maggiore di 0, lo stato di Suspend/Resume per il livello è OFF. Quando il conteggio è minore o uguale a 0, lo stato di Suspend/Resume è ON.

 Se lo stato di Start/Stop e lo stato di Suspend/Resume sono entrambi ON, lo stato di profilatura per il livello è ON. Affinché un thread venga incluso nella profilatura, gli stati dei livelli globale, processo e thread per il thread devono essere tutti ON.

## <a name="net-framework-equivalent"></a>Equivalente .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informazioni sulla funzione
 *Intestazione: dichiarata in VSPerf.h*

 Libreria di importazione: *VSPerf.lib*

## <a name="example"></a>Esempio
 L'esempio seguente illustra il metodo SuspendProfile. Questo esempio presuppone l'esecuzione di una chiamata precedente a StartProfile per il processo o thread identificato da [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
void ExerciseSuspendProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the
    // Suspend/Resume count; each call
    // to ResumeProfile subtracts 1.

    // Variables used to print output
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to SuspendProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = SuspendProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("SuspendProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Vedi anche
- [Visual Studio riferimento all'API del profiler (nativo)](../profiling/visual-studio-profiler-api-reference-native.md)
