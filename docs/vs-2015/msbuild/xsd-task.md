---
title: Attività XSD | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f5a6bf91c6e9218593031ff15f2b31822ea5fa1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532176"
---
# <a name="xsd-task"></a>Attività XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività XSD](https://docs.microsoft.com/visualstudio/msbuild/xsd-task).  
  
  
Esegue il wrapping dello strumento XML Schema Definition (xsd.exe), che genera file di schema o di classe da un'origine.  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente descrive i parametri dell'attività **XSD**.  
  
-   **AdditionalOptions**  
  
     Parametro **String** facoltativo.  
  
     Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, "*/opzione1 /opzione2 /opzione#*". Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XSD**.  
  
-   **GenerateFromSchema**  
  
     Parametro **String** facoltativo.  
  
     Specifica i tipi generati dallo schema specificato.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione XSD.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Lingua**  
  
     Parametro **String** facoltativo.  
  
     Specifica il linguaggio di programmazione da usare per il codice generato.  
  
     È possibile scegliere tra **CS** (C#, il linguaggio predefinito), **VB** (Visual Basic) o **JS** (JScript). È anche possibile specificare un nome completo per una classe che implementa `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
-   **Namespace**  
  
     Parametro **String** facoltativo.  
  
     Specifica lo spazio dei nomi del runtime per i tipi generati.  
  
-   **Sources**  
  
     Parametro `ITaskItem[]` obbligatorio.  
  
     Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.  
  
-   **SuppressStartupBanner**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.  
  
-   **TrackerLogDirectory**  
  
     Parametro **String** facoltativo.  
  
     Specifica la directory per il log di Tracker.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)



