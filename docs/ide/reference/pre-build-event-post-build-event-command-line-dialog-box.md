---
title: Finestra di dialogo della riga di comando eventi pre-compilazione post-compilazione
description: Informazioni su come è possibile pre-compilazione o post-compilazione eventi direttamente nella casella di modifica o come è possibile selezionare macro di pre-compilazione e post-compilazione da un elenco di macro disponibili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1cb0081c084549692b335edd414caa1eabba1225137030ecea04a1030004a468
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121334302"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione

È possibile digitare gli eventi pre-compilazione o post-compilazione per la [Pagina Eventi di compilazione, Creazione progetti (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) direttamente nella casella di modifica oppure selezionare le macro pre-compilazione e post-compilazione da un elenco di macro disponibili.

> [!NOTE]
> Gli eventi di pre-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata alcuna compilazione.

## <a name="ui-element-list"></a>Elenco degli elementi dell'interfaccia utente

**Casella di modifica della riga di comando**

Contiene gli eventi da eseguire per la pre-compilazione o la post-compilazione.

> [!NOTE]
> Aggiungere un'istruzione `call` prima di tutti gli eventi di compilazione che eseguono file con estensione BAT. Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

**Macro**

Espande la casella di modifica per visualizzare un elenco di macro che è possibile inserire nella casella di modifica della riga di comando.

**Tabella delle macro**

Elenca le macro disponibili e il relativo valore. Per la descrizione di ogni macro, vedere la sezione Macro più avanti. È possibile selezionare una sola macro per volta da inserire nella casella di modifica della riga di comando.

**Inserimento**

Inserisce nella casella di modifica della riga di comando la macro selezionata nella tabella delle macro.

### <a name="macros"></a>Macro

È possibile usare una qualsiasi di queste macro per specificare i percorsi dei file o ottenere il nome effettivo del file di input in caso di selezioni multiple. Le macro non fanno distinzione tra maiuscole e minuscole.

|Macro|Descrizione|
|-----------|-----------------|
|`$(ConfigurationName)`|Nome della configurazione di progetto corrente, ad esempio "Debug".|
|`$(OutDir)`|Percorso della directory del file di output, relativo alla directory del progetto. Viene risolto nel valore per la proprietà Directory di output. Include la barra rovesciata finale "\\".|
|`$(DevEnvDir)`|Directory di installazione di Visual Studio (definita con unità e percorso); include la barra rovesciata finale "\\".|
|`$(PlatformName)`|Nome della piattaforma di destinazione corrente. Ad esempio, "AnyCPU".|
|`$(ProjectDir)`|Directory del progetto (definita con unità e percorso); include la barra rovesciata finale "\\".|
|`$(ProjectPath)`|Nome del percorso assoluto del progetto (definito con unità, percorso, nome di base ed estensione di file).|
|`$(ProjectName)`|Nome base del progetto.|
|`$(ProjectFileName)`|Nome file del progetto (definito con nome di base ed estensione di file).|
|`$(ProjectExt)`|Estensione di file del progetto. È incluso il punto '.' prima dell'estensione.|
|`$(SolutionDir)`|Directory della soluzione (definita con unità e percorso); include la barra rovesciata finale "\\".|
|`$(SolutionPath)`|Nome del percorso assoluto della soluzione (definito con unità, percorso, nome di base ed estensione di file).|
|`$(SolutionName)`|Nome base della soluzione.|
|`$(SolutionFileName)`|Nome file della soluzione (definito con nome di base ed estensione di file).|
|`$(SolutionExt)`|Estensione di file della soluzione. È incluso il punto '.' prima dell'estensione.|
|`$(TargetDir)`|Directory del file di output principale per la build (definita con unità e percorso). Include la barra rovesciata finale "\\".|
|`$(TargetPath)`|Nome del percorso assoluto del file di output principale per la build (definito con unità, percorso, nome di base ed estensione di file).|
|`$(TargetName)`|Nome di base del file di output principale per la compilazione.|
|`$(TargetFileName)`|Nome file del file di output principale per la build (definito come nome di base ed estensione di file).|
|`$(TargetExt)`|Estensione di file del file di output principale per la compilazione. È incluso il punto '.' prima dell'estensione.|

## <a name="see-also"></a>Vedi anche

- [Specifica di eventi di compilazione personalizzati in Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [Pagina Eventi di compilazione, Progettazione progetti (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [Procedura: Specificare eventi di compilazione (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Procedura: Specificare eventi di compilazione (C#)](../../ide/how-to-specify-build-events-csharp.md)
