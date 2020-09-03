---
title: Impostare le configurazioni di debug e di versione | Microsoft Docs
ms.date: 10/05/2018
ms.topic: how-to
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 458e6cb4ebf882d2d9e331823cc4955143e7d5b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349159"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Impostare le configurazioni Debug e Release in Visual Studio

Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug. Compilare la versione di debug per il debug e la versione di rilascio per la distribuzione finale della versione.

Nella configurazione di debug il programma viene compilato con informazioni di debug simboliche complete e senza ottimizzazione. L'ottimizzazione rende più difficile il debug perché la relazione tra il codice sorgente e le istruzioni generate è più complessa.

La configurazione di rilascio del programma non dispone di informazioni di debug simboliche ed è completamente ottimizzata. Per il codice gestito e il codice C++, le informazioni di debug possono essere generate in file PDB, [a seconda delle opzioni del compilatore](#BKMK_symbols_release) utilizzate. La creazione di file con estensione PDB può essere utile se successivamente è necessario eseguire il debug della versione di rilascio.

Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

È possibile modificare la configurazione di compilazione nel menu **Build**, nella barra degli strumenti o nelle pagine di proprietà del progetto. Pagine delle proprietà del progetto sono specifici del linguaggio. La procedura riportata di seguito viene illustrato come modificare la configurazione di compilazione dal menu e barra degli strumenti. Per ulteriori informazioni su come modificare la configurazione della build nei progetti in linguaggi diversi, vedere la sezione [vedere anche](#see-also) di seguito.

## <a name="change-the-build-configuration"></a>Modificare la configurazione della build

Per modificare la configurazione della build, effettuare una delle operazioni seguenti:

* Scegliere **Configuration Manager**dal menu **Compila** , quindi selezionare **debug** o **rilascia**.

Oppure

* Sulla barra degli strumenti selezionare **Debug ** o **Release** nell'elenco **Configurazione soluzione**.

  ![configurazione della build della barra degli strumenti](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Genera i file di simboli (con estensione pdb) per una compilazione (C#, C++, Visual Basic, F #)

È possibile scegliere di generare i file di simboli (con estensione pdb) e le informazioni di debug da includere. Per la maggior parte dei tipi di progetto, il compilatore genera i file di simboli per impostazione predefinita per le build di debug e di rilascio, mentre altre impostazioni predefinite sono diverse per tipo di progetto e versione di Visual Studio.

> [!IMPORTANT]
> Il debugger caricherà solo un file con estensione pdb per un file eseguibile che corrisponde esattamente al file pdb creato alla compilazione del file eseguibile (il file pdb deve essere l'originale o una copia del file pdb originale). Per ulteriori informazioni, vedere [motivi per cui Visual Studio richiede che i file di simboli del debugger corrispondano esattamente ai file binari con cui sono stati compilati](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

Per ogni tipo di progetto è possibile impostare queste opzioni in modo diverso.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Genera i file di simboli per un progetto C#, ASP.NET o Visual Basic

Per informazioni dettagliate sulle impostazioni di progetto per le configurazioni di debug in C# o Visual Basic, vedere [impostazioni di progetto per una configurazione di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md) o [impostazioni di progetto per una configurazione](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)di debug di Visual Basic.

1. In Esplora soluzioni selezionare il progetto.

2. Selezionare l'icona delle **Proprietà** o premere **ALT + INVIO**.

3. Nel riquadro laterale scegliere **Compila** (o **Compila** in Visual Basic).

4. Nell'elenco **configurazione** scegliere **debug** o **rilascio**.

5. Selezionare il pulsante **Avanzate** o il pulsante **Opzioni di compilazione avanzate** in Visual Basic).

6. Nell'elenco **informazioni di debug** (o nell'elenco **genera informazioni di debug** in Visual Basic) scegliere **completo**, **solo PDB**o portabile **Portable**.

   Il formato portatile è il formato multipiattaforma più recente per .NET Core. Per altre informazioni sulle opzioni, vedere [finestra di dialogo Impostazioni di compilazione avanzate (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Genera PDB per le compilazioni in C #](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Compilare il progetto.

   Il compilatore crea i file di simboli nella stessa cartella del file eseguibile o del file di output principale.

### <a name="generate-symbol-files-for-a-c-project"></a>Genera i file di simboli per un progetto C++

1. In Esplora soluzioni selezionare il progetto.

2. Selezionare l'icona delle **Proprietà** o premere **ALT + INVIO**.

3. Nell'elenco **configurazione** scegliere **debug** o **rilascio**.

4. Nel riquadro laterale scegliere **linker > debug**, quindi selezionare le opzioni per **genera informazioni di debug**.

   Per informazioni dettagliate sulle impostazioni di progetto per le configurazioni di debug in C++, vedere [impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Configurare le opzioni per la **generazione di file di database di programma**.

   Nella maggior parte dei progetti C++, il valore predefinito è `$(OutDir)$(TargetName).pdb` , che genera i file con estensione PDB nella cartella di output.

   ![Genera PDB per le compilazioni in C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Compilare il progetto.

   Il compilatore crea i file di simboli nella stessa cartella del file eseguibile o del file di output principale.

## <a name="see-also"></a><a name="see-also"></a>Vedere anche

- [Specificare i file di simboli (con estensione pdb) e i file di origine nel debugger di Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)<br/>
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Impostazioni di progetto per una configurazione di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
