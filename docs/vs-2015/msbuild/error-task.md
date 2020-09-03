---
title: Attività Error | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b220d12b872a81cba5f46bd14fdebafaa58cf4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201804"
---
# <a name="error-task"></a>Attività Error
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interrompe una compilazione e registra un errore in base a un'istruzione condizionale valutata.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Error`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Code`|Parametro `String` facoltativo.<br /><br /> Codice errore da associare all'errore.|  
|`File`|Parametro `String` facoltativo.<br /><br /> Il nome del file che contiene l'errore. Se non viene indicato alcun nome file, verrà usato il file contenente l'attività di errore.|  
|`HelpKeyword`|Parametro `String` facoltativo.<br /><br /> Parola chiave della Guida da associare all'errore.|  
|`Text`|Parametro `String` facoltativo.<br /><br /> Il testo dell'errore caricato da [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] se il parametro `Condition` restituisce `true`.|  
  
## <a name="remarks"></a>Osservazioni  
 L'attività `Error` consente ai progetti [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] di inviare il testo dell'errore ai logger e di arrestare l'esecuzione della compilazione.  
  
 Se il parametro `Condition` restituisce `true`, la compilazione viene interrotta e viene registrato un errore. Se non esiste un parametro `Condition`, l'errore viene registrato e l'esecuzione della compilazione viene arrestata. Per altre informazioni sulla registrazione, vedere [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md) (Recupero di log di compilazione).  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente verifica che siano impostate tutte le proprietà richieste. In caso contrario, il progetto genera un evento di errore e registra il valore del parametro `Text` sull'attività `Error`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento attività](../msbuild/msbuild-task-reference.md)   
 [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)
