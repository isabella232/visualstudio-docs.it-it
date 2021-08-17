---
title: Impostare le configurazioni di debug e | Microsoft Docs
description: Impostare le configurazioni di debug e versione in Visual Studio. Si compila la versione di debug per il debug e la versione di rilascio per la distribuzione della versione finale.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4958501cd7a6b42e6e733193b0f80bd723cdae10
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128182"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Impostare le configurazioni Debug e Release in Visual Studio

Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug. Si compila la versione di debug per il debug e la versione di rilascio per la distribuzione della versione finale.

Nella configurazione di debug il programma viene compilato con informazioni di debug simboliche complete e senza ottimizzazione. L'ottimizzazione rende più difficile il debug perché la relazione tra il codice sorgente e le istruzioni generate è più complessa.

La configurazione del rilascio del programma non ha informazioni di debug simboliche ed è completamente ottimizzata. Per il codice gestito e il codice C++, le [](#BKMK_symbols_release) informazioni di debug possono essere generate nei file con estensione pdb, a seconda delle opzioni del compilatore usate. La creazione di file con estensione pdb può essere utile se in un secondo momento è necessario eseguire il debug della versione di .

Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

È possibile modificare la configurazione di compilazione nel menu **Build**, nella barra degli strumenti o nelle pagine di proprietà del progetto. Pagine delle proprietà del progetto sono specifici del linguaggio. La procedura riportata di seguito viene illustrato come modificare la configurazione di compilazione dal menu e barra degli strumenti. Per altre informazioni su come modificare la configurazione di compilazione nei progetti in linguaggi diversi, vedere la sezione Vedere [anche](#see-also) più avanti.

## <a name="change-the-build-configuration"></a>Modificare la configurazione della compilazione

Per modificare la configurazione di compilazione, eseguire una delle seguenti attività:

* Dal menu **Compila** **selezionare Gestione configurazione**, quindi selezionare **Debug** o **Versione**.

oppure

* Sulla barra degli strumenti selezionare **Debug** o **Release** nell'elenco **Configurazione soluzione**.

  ![configurazione della compilazione delle barre degli strumenti](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Generare file di simboli (con estensione pdb) per una compilazione (C#, C++, Visual Basic, F#)

È possibile scegliere di generare i file di simboli (con estensione pdb) e le informazioni di debug da includere. Per la maggior parte dei tipi di progetto, il compilatore genera i file di simboli per impostazione predefinita per le build di debug e versione, mentre altre impostazioni predefinite differiscono per tipo di progetto e Visual Studio versione.

> [!IMPORTANT]
> Il debugger caricherà solo un file con estensione pdb per un file eseguibile che corrisponde esattamente al file pdb creato alla compilazione del file eseguibile (il file pdb deve essere l'originale o una copia del file pdb originale). Per altre informazioni, vedere Perché Visual Studio i file di simboli del debugger in modo che corrispondano esattamente ai file binari con cui [sono stati compilati?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with).

Ogni tipo di progetto può avere un modo diverso di impostare queste opzioni.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generare file di simboli per un progetto C#, ASP.NET o Visual Basic

Per informazioni dettagliate sulle impostazioni del progetto per le configurazioni di debug in C# o Visual Basic, vedere impostazioni Project per una configurazione di [debug C#](../debugger/project-settings-for-csharp-debug-configurations.md) o impostazioni di Project per una configurazione di [debug](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)Visual Basic.

1. In Esplora soluzioni selezionare il progetto.

2. Selezionare **l'icona** Proprietà (o **premere ALT+INVIO).**

3. Nel riquadro laterale scegliere **Compila** (o **Compila** in Visual Basic).

4. **Nell'elenco Configurazione** scegliere **Debug** o **Rilascia**.

5. Selezionare il **pulsante Avanzate** (o il pulsante **Opzioni di** compilazione avanzate in Visual Basic).

6. **Nell'elenco Informazioni di** debug (o nell'elenco Genera informazioni di **debug** in Visual Basic), scegliere Completo **,** **Solo Pdb** o **Portabile**.

   Il formato portabile è il formato multipiattaforma più recente per .NET Core. Per altre informazioni sulle opzioni, vedere Finestra di dialogo Impostazioni [compilazione avanzata (C#).](../ide/reference/advanced-build-settings-dialog-box-csharp.md)

   ![Generare PDB per le compilazioni in C #](../debugger/media/dbg_project_properties_pdb_csharp.png "Generare PDBsForCSharp")

7. Compilare il progetto.

   Il compilatore crea i file di simboli nella stessa cartella del file eseguibile o del file di output principale.

### <a name="generate-symbol-files-for-a-c-project"></a>Generare file di simboli per un progetto C++

1. In Esplora soluzioni selezionare il progetto.

2. Selezionare **l'icona** Proprietà (o **premere ALT+INVIO).**

3. **Nell'elenco Configurazione** scegliere **Debug** o **Rilascia**.

4. Nel riquadro laterale scegliere **Linker**> Debug , quindi selezionare le opzioni per **Genera informazioni di debug**.

   Per informazioni dettagliate sulle impostazioni del progetto per le configurazioni di debug in C++, vedere Project per una configurazione di [debug C++.](../debugger/project-settings-for-a-cpp-debug-configuration.md)

5. Configurare le opzioni per **Genera file di database di programma**.

   Nella maggior parte dei progetti C++ il valore predefinito è `$(OutDir)$(TargetName).pdb` , che genera file con estensione pdb nella cartella di output.

   ![Generare PDB per le compilazioni in C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Compilare il progetto.

   Il compilatore crea i file di simboli nella stessa cartella del file eseguibile o del file di output principale.

## <a name="see-also"></a><a name="see-also"></a>Vedere anche

- [Specificare i file di simboli (con estensione pdb) e i file di origine nel debugger Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)<br/>
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Project per una configurazione di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Procedura: Creare e modificare configurazioni](../ide/how-to-create-and-edit-configurations.md)