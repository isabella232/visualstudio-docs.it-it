---
title: Risolvere i problemi e creare i log per problemi relativi a MSBuild
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: 24df9f7c44ea2dbb9e9899abf68823683422da71
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235069"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Risolvere i problemi e creare i log per problemi relativi a MSBuild

Le procedure seguenti consentono di diagnosticare i problemi di compilazione nel progetto di Visual Studio e, se necessario, di creare un log da inviare a Microsoft per ulteriori indagini.

## <a name="a-property-value-is-ignored"></a>Un valore di proprietà viene ignorato

Se una proprietà del progetto sembra essere impostata su un valore specifico, ma non ha alcun effetto in fase di compilazione, seguire questa procedura:

1. Aprire il prompt dei comandi per gli sviluppatori di Visual Studio corrispondente alla versione in uso di Visual Studio.
1. Eseguire il comando seguente, dopo aver sostituito i valori per il percorso della soluzione, la configurazione e il nome di progetto:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Questo comando genera un file di progetto msbuild "pre-elaborato" (out.xml). È possibile cercare una proprietà specifica in tale file per vedere dove è definita.

L'ultima definizione di una proprietà è quella utilizzata dalla compilazione. Se la proprietà è impostata due volte, il secondo valore sovrascrive il primo. Inoltre, MSBuild valuta il progetto in diversi passaggi:

- PropertyGroups e Imports
- ItemDefinitionGroups
- ItemGroups
- Targets

Considerato l'ordine seguente, quindi:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

Il valore di "MyMetadata" per "MyFile.txt" verrà valutato come "B" durante la compilazione (non "A" e non vuoto)

## <a name="incremental-build-is-building-more-than-it-should"></a>La compilazione incrementale include più elementi del necessario

Se MSBuild ricompila inutilmente un progetto o un elemento del progetto, creare un log di compilazione dettagliato o binario. È possibile cercare nel log il file che è stato creato o compilato inutilmente. L'output è simile al seguente:

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Se si sta compilando nell'IDE di Visual Studio (con visualizzazione dettagliata nella finestra di output), nella **finestra di output** viene indicato il motivo per cui ogni progetto non è aggiornato:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Creare un log msbuild binario

1. Aprire il prompt dei comandi per gli sviluppatori per la versione di Visual Studio in uso
1. Dal prompt dei comandi eseguire uno dei comandi seguenti. (Ricordarsi di usare i valori effettivi per il progetto e la configurazione.):

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    o

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Verrà creato un file Msbuild.binlog nella directory da cui è stato eseguito MSBuild. È possibile visualizzarlo e cercarlo tramite il [visualizzatore log strutturato di Msbuild](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Creare un log dettagliato

1. Dal menu principale di Visual Studio passare a **strumenti**  >  **Opzioni**  >  **progetti e soluzioni**  > **Compila ed Esegui**.
1. Impostare **Livello di dettaglio output in compilazione progetto MSBuild** su **Dettagliato** in entrambe le caselle combinate. Il primo controlla il livello di dettaglio della compilazione nel **finestra di output** e il secondo controlla il livello di dettaglio della compilazione nel \<projectname\> file. log creato nella directory intermedia di ogni progetto durante la compilazione.
2. Da un prompt dei comandi per gli sviluppatori di Visual Studio, immettere uno di questi comandi, sostituendo i valori effettivi per percorso e configurazione:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    o

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Verrà creato un file Msbuild.log nella directory da cui è stato eseguito msbuild.

## <a name="see-also"></a>Vedere anche

- [Risoluzione dei problemi di Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
