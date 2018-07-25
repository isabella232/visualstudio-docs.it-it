---
title: Attività Exec | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89a8fd27dbf16db2277b52b2def2fac1e9f06e68
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945205"
---
# <a name="exec-task"></a>Exec (attività)
Esegue il programma o il comando specificato con gli argomenti specificati.  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente descrive i parametri dell'attività `Exec`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Command`|Parametro `String` obbligatorio.<br /><br /> Uno o più comandi da eseguire. Possono essere comandi di sistema, ad esempio attrib, o file eseguibili, ad esempio *program.exe*, *runprogram.bat* o *setup.msi*.<br /><br /> Questo parametro può contenere più righe di comandi. In alternativa, è possibile includere più comandi in un file batch ed eseguirlo tramite questo parametro.|  
|`ConsoleOutput`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ogni output di elemento è una riga del flusso di output standard o di errore standard generato dallo strumento. Viene acquisito solo se `ConsoleToMsBuild` è impostato su `true`.|
|`ConsoleToMsBuild`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività acquisisce l'errore standard e l'output standard dello strumento e li rende disponibili nel parametro di output `ConsoleOutput`. Il valore predefinito è `false`.|
|`CustomErrorRegularExpression`|Parametro `String` facoltativo.<br /><br /> Specifica un'espressione regolare usata per individuare eventuali righe di errore nell'output dello strumento. È particolarmente utile per gli strumenti che consentono la generazione di output con formattazione insolita.|  
|`CustomWarningRegularExpression`|Parametro `String` facoltativo.<br /><br /> Specifica un'espressione regolare usata per individuare eventuali righe di avviso nell'output dello strumento. È particolarmente utile per gli strumenti che consentono la generazione di output con formattazione insolita.|  
|`EchoOff`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività non genererà la forma espansa di `Command` nel log di MSBuild. Il valore predefinito è `false`.|
|`ExitCode`|Parametro di sola lettura di output `Int32` facoltativo.<br /><br /> Specifica il codice di uscita fornito dal comando eseguito.|  
|`IgnoreExitCode`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il codice di uscita fornito dal comando eseguito viene ignorato. In caso contrario, viene restituito `false` se il comando eseguito restituisce un codice di uscita diverso da zero.|  
|`IgnoreStandardErrorWarningFormat`|Parametro `Boolean` facoltativo.<br /><br /> Se `false`, le righe dell'output che corrispondono al formato di errore/avviso standard vengono selezionate e registrate come errori/avvisi. Se `true`, disabilitare questo comportamento. Il valore predefinito è `false`.|  
|`Outputs`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi di output dell'attività. L'attività `Exec` non imposta questi elementi autonomamente, ma è possibile fornirli come se fossero stati impostati dall'attività, in modo che possano essere usati in una fase successiva del progetto.|  
|`StdErrEncoding`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica la codifica del flusso di errore standard dell'attività acquisito. Il valore predefinito è la codifica dell'output della console corrente.|  
|`StdOutEncoding`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica la codifica del flusso di output standard dell'attività acquisito. Il valore predefinito è la codifica dell'output della console corrente.|  
|`WorkingDirectory`|Parametro `String` facoltativo.<br /><br /> Specifica la directory in cui verrà eseguito il comando.|  
  
## <a name="remarks"></a>Note  
 Questa attività è utile nei casi in cui non è disponibile un'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] specifica per il processo che si vuole eseguire. Tuttavia, l'attività `Exec`, a differenza di un'attività più specifica, non può eseguire un'altra elaborazione o operazioni condizionali in base al risultato dello strumento o del comando eseguito.
  
 Anziché richiamare direttamente un processo, l'attività `Exec` chiama *cmd.exe*.  
  
 Oltre ai parametri elencati in questo documento, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente l'attività `Exec` viene usata per eseguire un comando.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
