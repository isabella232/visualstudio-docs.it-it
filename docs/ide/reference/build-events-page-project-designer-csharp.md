---
title: Pagina Eventi di compilazione, Progettazione progetti (C#)
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6629f41657a546ffb5fb48e0b6efb5f4f0dd50cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596879"
---
# <a name="build-events-page-project-designer-c"></a>Pagina Eventi di compilazione, Progettazione progetti (C#)

Usare la pagina **Eventi di compilazione** di **Creazione progetti** per specificare le istruzioni di configurazione della build. È anche possibile specificare le condizioni in cui vengono eseguiti gli eventi di post-compilazione. Per ulteriori informazioni, vedere [Procedura: specificare gli eventi di compilazione (C)](../../ide/how-to-specify-build-events-csharp.md) e Procedura: specificare gli eventi di [compilazione (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Configurazione**

Questo controllo non è modificabile in questa pagina. Per una descrizione di questo controllo, vedere [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Piattaforma**

Questo controllo non è modificabile in questa pagina. Per una descrizione di questo controllo, vedere [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Riga di comando eventi pre-compilazione**

Specifica i comandi da eseguire prima dell'avvio della compilazione. Per immettere comandi lunghi, fare clic su **Modifica pre-compilazione** per visualizzare la [finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Gli eventi di pre-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata alcuna compilazione.

**Riga di comando eventi post-compilazione**

Specifica i comandi da eseguire dopo il completamento della compilazione. Per digitare comandi lunghi, fare clic su **Modifica post-compilazione** per visualizzare la finestra di dialogo Riga di comando eventi **pre-compilazione/post-compilazione**.

> [!NOTE]
> Aggiungere un'istruzione `call` prima di tutti gli eventi di compilazione che eseguono file con estensione BAT. Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

**Esegui evento post-compilazione**

Specifica le condizioni seguenti per l'esecuzione dell'evento di post-compilazione, come illustrato in questa tabella.

|Opzione|Risultato|
|------------|------------|
|**Sempre**|L'evento di post-compilazione verrà sempre eseguito, indipendentemente dall'esito della compilazione.|
|**On successful build**|L'evento di post-compilazione verrà eseguito se la compilazione avrà esito positivo. L'evento verrà quindi eseguito anche per un progetto aggiornato, purché la compilazione abbia esito positivo.|
|**Quando la compilazione aggiorna l'output del progetto**|L'evento di post-compilazione verrà eseguito solo quando il file di output del compilatore (con estensione exe o dll) è diverso dal file di output del compilatore precedente. L'evento di post-compilazione non viene quindi eseguito se un progetto è aggiornato.|

## <a name="in-the-project-file"></a>Nel file di progetto

Nelle versioni precedenti di Visual Studio, quando si modifica l'impostazione **PreBuildEvent** `PreBuildEvent` o `PostBuildEvent` **PostBuildEvent** nell'IDE, Visual Studio aggiunge una proprietà o al file di progetto. Ad esempio, se l'impostazione della riga di comando PreBuildEvent nell'IDE è il seguente:So for example, if your **PreBuildEvent** command line setting in the IDE is follows:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

quindi l'impostazione del file di progetto è:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

Per i progetti .NET Core, Visual Studio 2019 (e Visual Studio 2017 negli aggiornamenti più recenti) aggiunge una destinazione MSBuild denominata `PreBuild` `PostBuild` o per le impostazioni **PreBuildEvent** e **PostBuildEvent.** Queste destinazioni usano gli attributi BeforeTargets e **AfterTargets,** riconosciuti da MSBuild.These targets use the **BeforeTargets** and AfterTargets attributes, which MSBuild recognizes. Ad esempio, per l'esempio precedente, Visual Studio genera ora il codice seguente:For example, for the preceding example, Visual Studio now generates the following code:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Per un evento di post-compilazione, utilizzare il nome `PostBuild` e impostare l'attributo `AfterTargets` su `PostBuildEvent`.

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Queste modifiche ai file di progetto sono state apportate per supportare i progetti in stile SDK. Se si esegue manualmente la migrazione di un file di progetto dal `PreBuildEvent` `PostBuildEvent` formato precedente al `PreBuild` `PostBuild` formato in stile SDK, è necessario eliminare le proprietà e e sostituirle con e come illustrato nel codice precedente. Per informazioni su come stabilire se il progetto è in stile SDK, vedere Controllare il formato del [progetto](/nuget/resources/check-project-format).

## <a name="see-also"></a>Vedere anche

- [Procedura: specificare eventi di compilazione (Visual Basic)How to: Specify Build Events (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Procedura: specificare gli eventi di compilazione (C](../../ide/how-to-specify-build-events-csharp.md)
- [Project Properties Reference](../../ide/reference/project-properties-reference.md) (Riferimenti alle proprietà di progetto)
- [Compilazione ed edificio](../../ide/compiling-and-building-in-visual-studio.md)
