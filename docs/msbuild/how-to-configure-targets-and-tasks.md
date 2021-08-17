---
title: 'Procedura: Configurare destinazioni e attività | Microsoft Docs'
description: Informazioni su come impostare le MSBuild da eseguire nell'ambiente di destinazione, indipendentemente dall'ambiente del computer di sviluppo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0e4da8eb39af573201ce4a7c88ec85d5775e48bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069238"
---
# <a name="how-to-configure-targets-and-tasks"></a>Procedura: Configurare destinazioni e attività

Alcune attività MSBuild possono essere impostate in modo da essere eseguite nell'ambiente a cui sono destinate, indipendentemente dall'ambiente del computer di sviluppo. Se ad esempio si usa un computer a 64 bit per creare un'applicazione destinata a un'architettura a 32 bit, le attività selezionate vengono eseguite in un processo a 32 bit.

> [!NOTE]
> Se un'attività di compilazione è scritta in un linguaggio .NET, ad esempio in Visual C# o Visual Basic, e non usa strumenti o risorse native, potrà essere eseguita in qualsiasi contesto di destinazione senza adattamento.

## <a name="usingtask-attributes-and-task-parameters"></a>Attributi UsingTask e parametri dell'attività

Gli attributi `UsingTask` seguenti interessano tutte le operazioni di un'attività in un determinato processo di compilazione:

- L'attributo `Runtime`, se presente, imposta la versione CLR (Common Language Runtime) e può assumere uno dei valori seguenti: `CLR2`, `CLR4`, `CurrentRuntime` o `*` (qualsiasi runtime).

- L'attributo `Architecture`, se presente, imposta la piattaforma e il numero di bit e può assumere uno dei valori seguenti: `x86`, `x64`, `CurrentArchitecture` o `*` (qualsiasi architettura).

- L'attributo `TaskFactory`, se presente, imposta la factory delle attività che crea ed esegue l'istanza dell'attività e può assumere solo il valore `TaskHostFactory`. Per altre informazioni, vedere la sezione [Factory di attività](#task-factories) più avanti in questo documento.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Per impostare il contesto di destinazione di una singola attività è possibile usare anche i parametri `MSBuildRuntime` e `MSBuildArchitecture`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Prima di eseguire un'attività, MSBuild cerca un attributo `UsingTask` corrispondente con lo stesso contesto di destinazione. Deve essere trovata una corrispondenza anche per i parametri specificati in `UsingTask` ma non nell'attività corrispondente, così come per i parametri specificati nell'attività ma non nell'attributo `UsingTask` corrispondente. Se non sono stati specificati valori di parametro né per `UsingTask` né per l'attività, l'impostazione predefinita dei valori è `*` (qualsiasi parametro).

> [!WARNING]
> Se sono presenti più elementi `UsingTask` e hanno tutti attributi `TaskName`, `Runtime` e `Architecture` corrispondenti, l'ultimo da valutare sostituisce gli altri.

 Se sono stati impostati parametri nell'attività, MSBuild tenta di trovare un elemento `UsingTask` che corrisponda, o almeno non sia in conflitto, con i parametri impostati. È possibile che più elementi `UsingTask` specifichino il contesto di destinazione per la stessa attività. Un'attività con vari file eseguibili per diversi ambienti di destinazione, ad esempio, avrebbe un aspetto simile al seguente:

```xml
<UsingTask TaskName="MyTool"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />

<UsingTask TaskName="MyTool"
    Runtime="CLR4"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />

<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>

```

## <a name="task-factories"></a>Factory di attività

Prima di eseguire un'attività, MSBuild verifica di essere stato designato per l'esecuzione nel contesto software corrente. In questo caso, MSBuild passa l'attività a AssemblyTaskFactory, che la esegue nel processo corrente; in caso contrario, MSBuild passa l'attività a TaskHostFactory, che la esegue in un processo corrispondente al contesto di destinazione. Anche se il contesto corrente e il contesto di destinazione corrispondono, è possibile imporre l'esecuzione out-of-process di un'attività (per motivi di isolamento, sicurezza o di altri tipo) impostando `TaskFactory` su `TaskHostFactory`.

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Parametri fantasma dell'attività

Come qualsiasi altro parametro dell'attività, `MSBuildRuntime` e `MSBuildArchitecture` possono essere impostati dalle proprietà di compilazione.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <FrameworkVersion>3.0</FrameworkVersion>
    </PropertyGroup>
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

A differenza di altri parametri di attività, `MSBuildRuntime` e `MSBuildArchitecture` non vengono visualizzati per l'attività stessa. Per scrivere un'attività che considera il contesto in cui viene eseguita, è necessario verificare il contesto tramite una chiamata a .NET Framework o usare le proprietà di compilazione per passare le informazioni sul contesto tramite altri parametri di attività.

> [!NOTE]
> Gli attributi `UsingTask` possono essere impostati dalle proprietà del set di strumenti o dell'ambiente.

I parametri `MSBuildRuntime` e `MSBuildArchitecture` offrono il metodo più flessibile per impostare il contesto di destinazione ma anche il più limitato relativamente all'ambito. Da un lato, poiché vengono impostati nell'istanza dell'attività e vengono valutati solo prima dell'esecuzione dell'attività, possono derivare il valore dall'ambito completo di proprietà disponibili in fase di valutazione e in fase di compilazione. Dall'altro, questi parametri vengono applicati solo a una particolare istanza di un'attività in una determinata destinazione.

> [!NOTE]
> I parametri dell'attività vengono valutati nel contesto del nodo padre, non nel contesto dell'host dell'attività. Le variabili di ambiente dipendenti dal runtime o dall'architettura, come ad esempio, il percorso di *Programmi*, restituiranno il valore che corrisponde al nodo padre. Tuttavia, se la stessa variabile di ambiente viene letta direttamente dall'attività, verrà valutata correttamente nel contesto dell'host di attività.

## <a name="see-also"></a>Vedi anche

- [Configurare destinazioni e attività](../msbuild/configuring-targets-and-tasks.md)
- [Elemento UsingTask](../msbuild/usingtask-element-msbuild.md)
