---
title: Impostazione del debug e rilascio delle configurazioni | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a65a3331c210bdfb4143ff890180fdc7d663229
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257225"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Impostazione del debug e rilascio delle configurazioni in Visual Studio

Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug. Si compila la versione di debug per il debug e la versione di rilascio per la distribuzione finale.

Nella configurazione di debug, il programma viene compilato con informazioni di debug complete sui simboli e senza ottimizzazione. L'ottimizzazione rende più difficile il debug perché la relazione tra il codice sorgente e le istruzioni generate è più complessa.

La configurazione di rilascio del programma è disponibile alcuna informazione di debug sui simboli ed è perfettamente ottimizzata. Eseguire il debug informazioni possono essere generate in file con estensione PDB [a seconda delle opzioni del compilatore](#BKMK_symbols_release) che vengono usate. Creazione di file con estensione PDB può essere utile se successivamente sarà necessario eseguire il debug della versione di rilascio.

Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

È possibile modificare la configurazione della build dal **compilazione** dal menu nella barra degli strumenti o nelle pagine delle proprietà del progetto. Pagine delle proprietà del progetto sono specifici del linguaggio. La procedura riportata di seguito viene illustrato come modificare la configurazione di compilazione dal menu e barra degli strumenti. Per altre informazioni su come modificare la configurazione di compilazione nei progetti in linguaggi diversi, vedere la [vedere anche](#see-also) sezione riportata di seguito.

## <a name="change-the-build-configuration"></a>Modificare la configurazione della build

Per modificare la configurazione della build, ovvero:

* Dal **compilare** dal menu **Configuration Manager**, quindi selezionare **Debug** o **versione**.

oppure

* Sulla barra degli strumenti, scegliere **eseguire il Debug** oppure **versione** dal **configurazioni soluzione** elenco.

  ![le barre degli strumenti di configurazione della build](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Generare i file di simboli (PDB) per una compilazione (C#, C++, Visual Basic, F#)

È possibile scegliere di generare file di simboli (PDB) e cosa includere informazioni di debug. Per la maggior parte dei tipi di progetto, il compilatore genera file di simboli per impostazione predefinita per il debug e build di rilascio, mentre altre impostazioni predefinite sono diversi dal tipo di progetto e la versione di Visual Studio.

> [!IMPORTANT]
> Il debugger caricherà solo un file con estensione pdb per un file eseguibile che corrisponde esattamente al file pdb creato alla compilazione del file eseguibile (il file pdb deve essere l'originale o una copia del file pdb originale). Per altre informazioni, vedere [perché Visual Studio richiede file di simboli del debugger una corrispondenza esatta tra i file binari con cui sono stati creati?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Ogni tipo di progetto può avere un modo diverso di impostazione di queste opzioni.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generare file di simboli per un progetto c#, ASP.NET o Visual Basic

Per informazioni dettagliate sulle impostazioni di progetto per le configurazioni di debug in c# o Visual Basic, vedere [configurazione di debug di impostazioni di progetto per c#](../debugger/project-settings-for-csharp-debug-configurations.md) o [impostazioni di progetto per Visual Basic debug configuration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Selezionare il progetto in Esplora soluzioni.

2. Selezionare il **delle proprietà** icona (o premere **Alt + Invio**).

3. Nel riquadro laterale, scegliere **compilare** (o **compilare** in Visual Basic).

4. Nel **Configuration** scegliere **Debug** oppure **versione**.

5. Selezionare il **avanzate** pulsante (o il **opzioni di compilazione avanzate** pulsante in Visual Basic).

6. Nel **le informazioni di debug** elenco (o il **enera informazioni di debug** elenco in Visual Basic), scegliere **completo**, **Pdb-only**, o **Portabile**.

   Il formato portabile è il più recente formato lo sviluppo multipiattaforma per .NET Core. Per altre informazioni sulle opzioni, vedere [finestra di dialogo Impostazioni di compilazione avanzate (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generare file PDB per le compilazioni in c#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Compilazione del progetto.

   Il compilatore crea i file di simboli nella stessa cartella del file eseguibile o file di output principale.

### <a name="generate-symbol-files-for-a-c-project"></a>Generare file di simboli per un progetto C++

1. Selezionare il progetto in Esplora soluzioni.

2. Selezionare il **delle proprietà** icona (o premere **Alt + Invio**).

3. Nel **Configuration** scegliere **Debug** oppure **versione**.

4. Nel riquadro laterale, scegliere **Linker > Debugging**, quindi selezionare le opzioni per **genera informazioni di Debug**.

   Per informazioni dettagliate sulle impostazioni di progetto per le configurazioni di debug in C++, vedere [configurazione di impostazioni di progetto per C++ debug](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Configurare le opzioni relative **genera file di Database di programma**.

   Nella maggior parte dei progetti C++, il valore predefinito è `$(OutDir)$(TargetName).pdb`, che genera file con estensione pdb nella cartella di output.

   ![Generare file PDB per le compilazioni in C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Compilazione del progetto.

   Il compilatore crea i file di simboli nella stessa cartella del file eseguibile o file di output principale.

## <a name="see-also"></a>Vedere anche
 
[Specifica i file di simboli (PDB) e i file di origine nel debugger di Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
[Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)<br/>
[Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
[Impostazioni di progetto per una configurazione di debug c#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
[Impostazioni di progetto per una configurazione di debug di Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
[Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
