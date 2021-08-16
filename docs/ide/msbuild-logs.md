---
title: Risolvere i problemi e creare i log per problemi relativi a MSBuild
description: Informazioni su come diagnosticare i problemi di compilazione nel progetto Visual Studio e, se necessario, creare un log da inviare a Microsoft per l'analisi.
ms.custom: SEO-VS-2020
ms.date: 02/08/2021
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: efa2ba6a298c4e3326b8a43d3fe6e8ecef0fb214beba6e1b0aaaa26643b982ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413015"
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

## <a name="create-a-binary-msbuild-log-at-the-command-prompt"></a>Creare un log MSBuild binario al prompt dei comandi

1. Aprire il prompt dei comandi per gli sviluppatori per la versione di Visual Studio in uso

1. Dal prompt dei comandi eseguire uno dei comandi seguenti. (Ricordarsi di usare i valori effettivi per il progetto e la configurazione.):

   ```cmd
   Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
   ```

   oppure

   ```cmd
   Msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
   ```

Viene creato un file *msbuild.binlog* nella directory da cui è stato eseguito MSBuild file.

## <a name="create-a-binary-msbuild-log-by-using-the-project-system-tools-extension"></a>Creare un log MSBuild binario usando l'estensione Project System Tools

1. Scaricare e installare [l'estensione Project System Tools](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools).

1. Dopo aver installato l'estensione, alcuni nuovi elementi vengono visualizzati **nel**  >  menu Visualizza **Windows.**

   ![Altri Windows menu](../ide/media/view-menu.png)

1. Selezionare **Visualizza altri**  >  **Windows** di compilazione  >  **per** visualizzare la finestra **Registrazione** compilazione in Visual Studio. Scegliere la prima icona della barra degli strumenti per avviare la registrazione di compilazioni sia normali che in fase di progettazione nel sistema del progetto.

   ![Finestra Di registrazione compilazione](../ide/media/build-logging-click-to-record.png)

1. Una volta registrata, una compilazione viene visualizzata nella finestra Registrazione compilazione. Fare clic con il pulsante destro del mouse sull'elemento e scegliere **Salva** log dal menu di scelta rapida per salvare il file *con estensione binlog.*

   ![Menu di scelta rapida per la registrazione della compilazione](../ide/media/build-logging-context-menu.png)

È possibile visualizzare ed eseguire ricerche *nei file con estensione binlog* usando MSBuild [Visualizzatore log strutturato](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Creare un log dettagliato

1. Dal menu Visual Studio menu principale, passare **a** Strumenti  >  **Opzioni** Progetti  >  **e soluzioni**  > **Compilare ed eseguire**.
1. Impostare **Livello di dettaglio output in compilazione progetto MSBuild** su **Dettagliato** in entrambe le caselle combinate. La prima controlla il livello di dettaglio della compilazione nel **Finestra di output** e la seconda controlla il livello di dettaglio della compilazione nel file con estensione log creato nella directory intermedia di ogni progetto durante \<projectname\> la compilazione.
2. Da un prompt dei comandi per gli sviluppatori di Visual Studio, immettere uno di questi comandi, sostituendo i valori effettivi per percorso e configurazione:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    oppure

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Verrà creato un file Msbuild.log nella directory da cui è stato eseguito msbuild.

## <a name="see-also"></a>Vedi anche

- [Visual Studio risoluzione dei problemi](/troubleshoot/visualstudio/welcome-visual-studio/)
