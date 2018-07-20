---
title: Impostazione del debug e rilascio delle configurazioni | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
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
ms.openlocfilehash: ea27fdccaadc70f22d9c9c02d75ddef98a11be13
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153098"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Impostazione del debug e rilascio delle configurazioni in Visual Studio
Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug. Come indicato dai nomi, la versione di debug viene compilata per eseguire il debug, mentre quella di rilascio viene compilata per la distribuzione finale.  
  
La configurazione di debug del programma è compilata con le informazioni complete di debug sui simboli e senza ottimizzazione. L'ottimizzazione rende più difficile il debug perché la relazione tra il codice sorgente e le istruzioni generate è più complessa.  
  
La configurazione di rilascio del programma non contiene alcuna informazione di debug sui simboli ed è perfettamente ottimizzata. Eseguire il debug informazioni possono essere generate in file con estensione PDB [a seconda delle opzioni del compilatore](#BKMK_symbols_release) che vengono usate. Creazione di file con estensione PDB può essere molto utile se successivamente sarà necessario eseguire il debug della versione di rilascio.  
  
Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
È possibile modificare la configurazione della build dal **compilazione** dal menu nella barra degli strumenti o nelle pagine delle proprietà del progetto. Pagine delle proprietà del progetto sono specifici del linguaggio. La procedura riportata di seguito viene illustrato come modificare la configurazione di compilazione dal menu e barra degli strumenti. Per altre informazioni su come modificare la configurazione di compilazione nei progetti in linguaggi diversi, vedere la sezione Vedere anche seguente.  
  
## <a name="change-the-build-configuration"></a>Modificare la configurazione della build  
  
1.  Dal **compilare** dal menu **Configuration Manager**, quindi selezionare **Debug** o **versione**.  
  
2.  Sulla barra degli strumenti, scegliere **eseguire il Debug** oppure **versione** dal **configurazioni soluzione** casella di riepilogo.  
  
     ![configurazione di compilazione sulla barra degli strumenti](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Questa procedura guidata non è disponibile nelle edizioni Express. È possibile usare la **Compila soluzione F6** e **Avvia debug F5** voci di menu per scegliere la configurazione.

## <a name="BKMK_symbols_release"></a>Generare i file di simboli (PDB) per una compilazione

Per la maggior parte dei tipi di progetto, i file con estensione PDB vengono generati per impostazione predefinita per debug e build di rilascio, ma le impostazioni predefinite sono diverse a seconda del tipo di progetto specifici e la versione di Visual Studio. È possibile configurare se il compilatore genera un file con estensione pdb e il tipo di informazioni di debug da includere.

> [!IMPORTANT] 
> Il debugger caricherà solo un file con estensione pdb per un file eseguibile che corrisponde esattamente al file pdb creato alla compilazione del file eseguibile (il file pdb deve essere l'originale o una copia del file pdb originale). Per altre informazioni, vedere il post del blog sulla [necessità di creare una corrispondenza esatta tra i file di simboli del debugger e i file binari con cui sono stati creati](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Ogni tipo di progetto può avere un modo diverso di impostazione di queste opzioni.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generare file di simboli per un progetto c#, ASP.NET o Visual Basic

Per informazioni dettagliate sulle impostazioni di progetto per le configurazioni di debug in c#, vedere [impostazioni per una configurazione di Debug c# del progetto](../debugger/project-settings-for-csharp-debug-configurations.md). Per Visual Basic, vedere [in questo argomento](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Fare clic sul progetto in Esplora soluzioni e scegliere **proprietà**.

2. Scegliere una **Release** o **Debug** compilare dal **configurazione** elenco.

2. Scegli **compilare** le impostazioni e quindi fare clic sui **avanzate** pulsante.

    In Visual Basic, è possibile scegliere il **Compile** le impostazioni e i **opzioni di compilazione avanzate** pulsante invece.

3. Scegliere **completa**, **portabile**, o **pdb_only** nel **le informazioni di debug** casella di riepilogo (**Generainformazionididebug** in Visual Basic).

    Il formato portabile è il più recente formato lo sviluppo multipiattaforma per .NET Core. Per altre informazioni sulle opzioni, vedere [finestra di dialogo Impostazioni di compilazione avanzate (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![Generare file PDB per le compilazioni in c#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Compilazione del progetto.

    I file di simboli vengono creati nella stessa cartella del file eseguibile o file di output principale.

### <a name="generate-symbol-files-for-a-c-project"></a>Generare file di simboli per un progetto C++

1. Fare clic sul progetto in Esplora soluzioni e scegliere **proprietà**.

2. Scegliere una **Release** o **Debug** compilare dal **configurazione** elenco.

2. Sotto **Linker > Debugging**, selezionare opzioni per desiderate **genera informazioni di Debug**.

    Per informazioni dettagliate sulle impostazioni di progetto per le configurazioni di debug in C++, vedere [impostazioni di Project per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Configurare le opzioni per generare file di Database di programma

    Nella maggior parte dei progetti C++, il valore predefinito è `$(OutDir)$(TargetName).pdb`, che genera file con estensione pdb nella cartella di output.

    ![Generare file PDB per le compilazioni in C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Compilazione del progetto.

    I file di simboli vengono creati nella stessa cartella del file eseguibile o file di output principale.
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i file di simboli (PDB) e i file di origine nel debugger di Studio di strumenti](../debugger/debugger-settings-and-preparation.md)  
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Impostazioni di progetto per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)
