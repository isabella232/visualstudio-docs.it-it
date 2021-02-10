---
title: Attività XSD | Microsoft Docs
description: Informazioni su come MSBuild utilizza l'attività XSD per eseguire il wrapping dello strumento XML Schema Definition xsd.exe, che genera file di schema o di classe da un'origine.
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
ms.workload:
- multiple
ms.openlocfilehash: 7227fff5dd4c58e1bce81ef8cad5c32f854abf55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960325"
---
# <a name="xsd-task"></a>XSD (attività)

Esegue il wrapping dello strumento XML Schema Definition (*xsd.exe*), che genera file di schema o di classe da un'origine.

> [!NOTE]
> A partire da Visual Studio 2017, il supporto dei progetti C++ per *xsd.exe* è deprecato. È comunque possibile usare le API **Microsoft.VisualC.CppCodeProvider** aggiungendo manualmente *CppCodeProvider.dll* alla Global Assembly Cache.

## <a name="parameters"></a>Parametri

 La tabella seguente descrive i parametri dell'attività **XSD**.

- **AdditionalOptions**

     Parametro **stringa** facoltativo.

     Un elenco di opzioni come specificato sulla riga di comando. Ad esempio,/ \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XSD**.

- **GenerateFromSchema**

  Parametro **stringa** facoltativo.

  Specifica i tipi generati dallo schema specificato.

  Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione XSD.

  - **classi**  -  **/Classes**

  - **set di dati**  -  **/DataSet**

- **Lingua**

     Parametro **stringa** facoltativo.

     Specifica il linguaggio di programmazione da usare per il codice generato.

     È possibile scegliere tra **CS** (C#, il linguaggio predefinito), **VB** (Visual Basic) o **JS** (JScript). È anche possibile specificare un nome completo per una classe che implementa `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Namespace**

     Parametro **stringa** facoltativo.

     Specifica lo spazio dei nomi del runtime per i tipi generati.

- **recenti**

     Parametro `ITaskItem[]` obbligatorio.

     Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.

- **SuppressStartupBanner**

     Parametro **booleano** facoltativo.

     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.

- **TrackerLogDirectory**

     Parametro **stringa** facoltativo.

     Specifica la directory per il log di Tracker.

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
