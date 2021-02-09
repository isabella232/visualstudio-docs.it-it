---
title: Attività Exec | Microsoft Docs
description: Informazioni su come usare l'attività di MSBuild Exec per eseguire un programma o un comando specifico usando gli argomenti specificati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 785d1bcfb8fdce5b09e749dcca17ff476a5d3f48
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877161"
---
# <a name="exec-task"></a>Exec (attività)

Esegue il programma o il comando specificato con gli argomenti specificati.

## <a name="parameters"></a>Parametri

La tabella seguente descrive i parametri dell'attività `Exec`.

|Parametro|Descrizione|
|---------------|-----------------|
|`Command`|Parametro `String` obbligatorio.<br /><br /> Uno o più comandi da eseguire. Questi possono essere comandi di sistema, ad esempio attrib, o un eseguibile, ad esempio *program.exe*, *runprogram.bat* o *setup.msi*.<br /><br /> Questo parametro può contenere più righe di comandi. In alternativa, è possibile includere più comandi in un file batch ed eseguirlo tramite questo parametro.|
|`ConsoleOutput`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ogni output di elemento è una riga del flusso di output standard o di errore standard generato dallo strumento. Viene acquisito solo se `ConsoleToMsBuild` è impostato su `true`.|
|`ConsoleToMsBuild`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività acquisisce l'errore standard e l'output standard dello strumento e li rende disponibili nel parametro di output `ConsoleOutput`.<br /><br />Impostazione predefinita: `false`.|
|`CustomErrorRegularExpression`|Parametro `String` facoltativo.<br /><br /> Specifica un'espressione regolare usata per individuare eventuali righe di errore nell'output dello strumento. È particolarmente utile per gli strumenti che consentono la generazione di output con formattazione insolita.<br /><br />Valore predefinito: `null` (nessuna elaborazione personalizzata).|
|`CustomWarningRegularExpression`|Parametro `String` facoltativo.<br /><br /> Specifica un'espressione regolare usata per individuare eventuali righe di avviso nell'output dello strumento. È particolarmente utile per gli strumenti che consentono la generazione di output con formattazione insolita.<br /><br />Valore predefinito: `null` (nessuna elaborazione personalizzata).|
|`EchoOff`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività non genererà la forma espansa di `Command` nel log di MSBuild.<br /><br />Impostazione predefinita: `false`.|
|`ExitCode`|Parametro di sola lettura di output `Int32` facoltativo.<br /><br /> Specifica il codice di uscita fornito dal comando eseguito, ad eccezione del fatto che se l'attività ha registrato errori, ma il processo ha un codice di uscita pari a 0 (esito positivo), `ExitCode` viene impostato su-1.|
|`IgnoreExitCode`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il codice di uscita fornito dal comando eseguito viene ignorato. In caso contrario, viene restituito `false` se il comando eseguito restituisce un codice di uscita diverso da zero.<br /><br />Impostazione predefinita: `false`.|
|`IgnoreStandardErrorWarningFormat`|Parametro `Boolean` facoltativo.<br /><br /> Se `false`, le righe dell'output che corrispondono al formato di errore/avviso standard vengono selezionate e registrate come errori/avvisi. Se `true`, disabilitare questo comportamento.<br /><br />Impostazione predefinita: `false`.|
|`Outputs`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi di output dell'attività. L'attività `Exec` non imposta questi elementi autonomamente, ma è possibile fornirli come se fossero stati impostati dall'attività, in modo che possano essere usati in una fase successiva del progetto.|
|`StdErrEncoding`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica la codifica del flusso di errore standard dell'attività acquisito. Il valore predefinito è la codifica dell'output della console corrente.|
|`StdOutEncoding`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica la codifica del flusso di output standard dell'attività acquisito. Il valore predefinito è la codifica dell'output della console corrente.|
|`WorkingDirectory`|Parametro `String` facoltativo.<br /><br /> Specifica la directory in cui verrà eseguito il comando.<br /><br />Valore predefinito: directory di lavoro corrente del progetto.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="remarks"></a>Commenti

Questa attività è utile quando una specifica attività MSBuild per il processo che si desidera eseguire non è disponibile. Tuttavia, l'attività `Exec`, a differenza di un'attività più specifica, non può eseguire un'altra elaborazione o operazioni condizionali in base al risultato dello strumento o del comando eseguito.

L' `Exec` attività chiama *cmd.exe* anziché richiamare direttamente un processo.

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

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
