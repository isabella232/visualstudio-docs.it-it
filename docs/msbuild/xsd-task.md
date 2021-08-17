---
title: Attività XSD | Microsoft Docs
description: Informazioni su MSBuild'attività XSD per eseguire il wrapping dello strumento XML Schema Definition xsd.exe, che genera file di schema o di classe da un'origine.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.topic: reference
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
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 9af55b62782a8d10b2e193b29bb9d8fade5b9aad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039891"
---
# <a name="xsd-task"></a>XSD (attività)

Esegue il wrapping dello strumento XML Schema Definition (*xsd.exe*), che genera file di schema o di classe da un'origine.

> [!NOTE]
> A partire da Visual Studio 2017, il supporto dei progetti C++ per *xsd.exe* è deprecato. È comunque possibile usare le API **Microsoft.VisualC.CppCodeProvider** aggiungendo manualmente *CppCodeProvider.dll* alla Global Assembly Cache.

## <a name="parameters"></a>Parametri

 La tabella seguente descrive i parametri dell'attività **XSD**.

- **AdditionalOptions**

     Parametro **String** facoltativo.

     Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, / \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XSD**.

- **GenerateFromSchema**

  Parametro **String** facoltativo.

  Specifica i tipi generati dallo schema specificato.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione XSD.

  - **classi**  -  **/classes**

  - **set di dati**  -  **/dataset**

- **Lingua**

     Parametro **String** facoltativo.

     Specifica il linguaggio di programmazione da usare per il codice generato.

     È possibile scegliere tra **CS** (C#, il linguaggio predefinito), **VB** (Visual Basic) o **JS** (JScript). È anche possibile specificare un nome completo per una classe che implementa `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Namespace**

     Parametro **String** facoltativo.

     Specifica lo spazio dei nomi del runtime per i tipi generati.

- **recenti**

     Parametro `ITaskItem[]` obbligatorio.

     Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.

- **SuppressStartupBanner**

     Parametro **booleano** facoltativo.

     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.

- **TrackerLogDirectory**

     Parametro **String** facoltativo.

     Specifica la directory per il log di Tracker.

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
