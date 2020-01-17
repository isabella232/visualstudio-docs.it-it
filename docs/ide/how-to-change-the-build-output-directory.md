---
title: "Procedura: modificare la directory dell'output compilato"
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37342796f2dd94138136bb837cf6007d19d350c4
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114259"
---
# <a name="how-to-change-the-build-output-directory"></a>Procedura: modificare la directory dell'output compilato

Il percorso dell'output generato dal progetto può essere specificato a livello di singole configurazioni (per debug e/o rilascio).

## <a name="change-the-build-output-directory"></a>Modificare la directory di output della compilazione

1. Per aprire le pagine delle proprietà del progetto fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.

2. Selezionare la scheda appropriata in base al tipo di progetto:

   - Per C#, selezionare la scheda **Compila**.
   - Per Visual Basic, selezionare la scheda **Compilazione**.
   - Per C++ o JavaScript, selezionare la scheda **Generale**.

3. Nell'elenco a discesa della configurazione nella parte superiore scegliere la configurazione per cui si vuole modificare il percorso di output (**Debug**, **Rilascio** o **Tutte le configurazioni**).

4. Individuare la voce relativa al percorso di output nella pagina, che è diversa a seconda del tipo di progetto:

   - **Percorso di output** per i progetti C# e JavaScript
   - **Percorso dell'output di compilazione** per i progetti Visual Basic
   - **Directory di output** per i progetti Visual C++

   Digitare il percorso per generare l'output (assoluto o relativo alla directory di progetto radice), oppure scegliere **Sfoglia** per passare alla relativa cartella.

   ![Proprietà Percorso di output per un progetto Visual Studio C#](media/output-path.png)
   
   > [!NOTE]
   > In alcuni progetti, per impostazione predefinita, il Framework e il runtime vengono inclusi nel percorso di compilazione. Per modificare questa operazione, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni**, scegliere **modifica file di progetto**e aggiungere quanto segue:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Se l'output non viene generato nel percorso specificato, assicurarsi di compilare la configurazione corrispondente, ad esempio **Debug** o **Rilascio**, selezionandola nella barra dei menu di Visual Studio.
>
> ![Selezione della configurazione della build in Visual Studio 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Vedere anche

- [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Pagina delle proprietà Generale (Progetto)](/cpp/build/reference/general-property-page-project)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
