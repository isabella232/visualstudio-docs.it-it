---
title: StartProfile| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 994cde18cfe304add796bffa74d2a327e1c63f45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199748"
---
# <a name="startprofile"></a>StartProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La funzione `StartProfile` imposta il contatore su 1 (On) per il livello di profilatura specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametri  
 `Level`  
  
 Indica il livello di profilatura a cui può essere applicata la raccolta di dati sulle prestazioni. Gli enumeratori **PROFILE_CONTROL_LEVEL** seguenti possono essere usati per indicare uno dei tre livelli a cui può essere applicata la raccolta di dati sulle prestazioni:  
  
|Enumerator|DESCRIZIONE|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Impostazione del livello globale con effetti su tutti i processi e i thread nell'esecuzione della profilatura.|  
|PROFILE_PROCESSLEVEL|Impostazione del livello processo con effetti su tutti i thread che fanno parte del processo specificato.|  
|PROFILE_THREADLEVEL|Impostazione del livello thread con effetti sul thread specificato.|  
  
 `dwId`  
  
 Identificatore del processo o del thread generato dal sistema.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 La funzione indica esito l'esito positivo o negativo usando l'enumerazione **PROFILE_COMMAND_STATUS**. Il valore restituito può essere uno dei seguenti:  
  
|Enumerator|DESCRIZIONE|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|L'ID dell'elemento di profilatura non esiste.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Il livello di profilatura specificato non esiste.|  
|PROFILE_ERROR_MODE_NEVER|La modalità di profilatura è stata impostata su NEVER al momento della chiamata della funzione.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|La chiamata della funzione di profilatura, il livello di profilatura o la combinazione di chiamata e livello non sono ancora stati implementati.|  
|PROFILE_OK|La chiamata è stata completata correttamente.|  
  
## <a name="remarks"></a>Osservazioni  
 StartProfile e StopProfile controllano lo stato di Start/Stop per il livello di profilatura. Il valore predefinito di Start/Stop è 1. Il valore iniziale può essere modificato nel Registro di sistema. Ogni chiamata a StartProfile imposta Start/Stop su 1. Ogni chiamata a StopProfile lo imposta su 0.  
  
 Quando Start/Stop è maggiore di 0, lo stato di Start/Stop per il livello è impostato su ON. Quando è minore o uguale a 0, lo stato di Start/Stop è OFF.  
  
 Se lo stato di Start/Stop e lo stato di Suspend/Resume sono entrambi ON, lo stato di profilatura per il livello è ON. Affinché un thread venga incluso nella profilatura, gli stati dei livelli globale, processo e thread per il thread devono essere ON.  
  
## <a name="net-framework-equivalent"></a>Equivalente .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informazioni sulla funzione  
 Intestazione: dichiarata in VSPerf.h  
  
 Libreria di importazione: VSPerf.lib  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra la chiamata della funzione StartProfile.  
  
```  
void ExerciseStartProfile()  
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
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per le API del profiler di Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)
