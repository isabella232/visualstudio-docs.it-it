---
title: 'Procedura: Set di configurazioni di Debug e rilascio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da8b3b32eae5d3045216f562dc7db25fb1f3264a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048192"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Procedura: Set di configurazioni di Debug e rilascio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug. Come indicato dai nomi, la versione di debug viene compilata per eseguire il debug, mentre quella di rilascio viene compilata per la distribuzione finale.  
  
 La configurazione di debug del programma è compilata con le informazioni complete di debug sui simboli e senza ottimizzazione. L'ottimizzazione rende più difficile il debug perché la relazione tra il codice sorgente e le istruzioni generate è più complessa.  
  
 La configurazione di rilascio del programma non contiene alcuna informazione di debug sui simboli ed è perfettamente ottimizzata. Le informazioni di debug possono essere generate in file PDB, in base alle opzioni del compilatore utilizzate. La creazione di file PDB può essere molto utile se successivamente sarà necessario eseguire il debug della versione di rilascio.  
  
 Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
 È possibile modificare la configurazione della build dal **compilazione** dal menu nella barra degli strumenti o nelle pagine delle proprietà del progetto. Pagine delle proprietà del progetto sono specifici del linguaggio. La procedura riportata di seguito viene illustrato come modificare la configurazione di compilazione dal menu e barra degli strumenti. Per ulteriori informazioni su come modificare la configurazione di compilazione nei progetti in linguaggi diversi, vedere la sezione Argomenti correlati.  
  
### <a name="to-change-the-build-configuration"></a>Per modificare la configurazione di compilazione  
  
1. Dal menu Compila: fare clic su **compilare / Configuration Manager**, quindi selezionare **Debug** oppure **versione**.  
  
2. Sulla barra degli strumenti, scegliere **eseguire il Debug** oppure **versione** dal **configurazioni soluzione** casella di riepilogo.  
  
     ![configurazione di compilazione sulla barra degli strumenti](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Questa procedura guidata non è disponibile nelle edizioni Express. È possibile usare la **Compila soluzione F6** e **Avvia debug F5** voci di menu per scegliere la configurazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Eseguire il debug e il rilascio delle configurazione del progetto](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)
