---
title: Gestire le proprietà di progetti e soluzioni
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01fcdc09c9d3ee4f5a38a95ef4304bfdf537d527
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591307"
---
# <a name="manage-project-and-solution-properties"></a>Gestire le proprietà di progetti e soluzioni

Le proprietà dei progetti governano molti aspetti della compilazione, del debug, del test e della distribuzione. Alcune proprietà sono comuni tra tutti i tipi di progetto e altre sono univoche di piattaforme o linguaggi specifici. Per accedere alle proprietà del progetto, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà** oppure digitare **proprietà** nella casella di ricerca sulla barra dei menu e scegliere **Finestra Proprietà** nei risultati.

![Menu di scelta rapida del progetto](../ide/media/vs2015_proj_prop_menu.gif)

I progetti .NET potrebbero anche avere un nodo di proprietà nell'albero del progetto.

![Nodo Proprietà nell'albero Esplora soluzioni](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Gestire le proprietà di progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Proprietà progetto

Le proprietà del progetto sono organizzate in gruppi e ogni gruppo ha una propria pagina delle proprietà. Le pagine possono essere diverse a seconda del linguaggio e del tipo di progetto.

### <a name="c-visual-basic-and-f-projects"></a>Progetti C#, Visual Basic e F#

Nei progetti di Visual Basic, Visual Basic e F , le proprietà vengono esposte in **Progettazione progetti**. Nella figura seguente viene illustrata la pagina delle proprietà **Compilazione** per un progetto WPF in C .

![Progettazione progetti di Visual Studio](../ide/media/vs2015_proppage_build.png)

Per informazioni su ognuna delle pagine delle proprietà in **Progettazione progetti**, vedere Informazioni di riferimento sulle [proprietà del progetto](../ide/reference/project-properties-reference.md).

> [!TIP]
> Le soluzioni hanno alcune proprietà e così fanno gli elementi di progetto; Queste proprietà sono accessibili nella [finestra Proprietà](../ide/reference/properties-window.md), non in **Progettazione progetti**.

### <a name="c-and-javascript-projects"></a>Progetti C++ e JavaScript

I progetti C++ e JavaScript hanno un'interfaccia utente differente per la gestione delle proprietà del progetto. Questa illustrazione mostra la pagina delle proprietà di un progetto C++ (le pagine JavaScript sono simili):

![Proprietà dei progetti Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png)

Per informazioni sulle proprietà di progetto C++, vedere [Utilizzo di proprietà di progetto (C++)](/cpp/build/working-with-project-properties). Per ulteriori informazioni sulle proprietà JavaScript, consultate [Pagine delle proprietà, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Proprietà della soluzione

Per accedere alle proprietà della soluzione, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Proprietà**. Nella finestra di dialogo è possibile impostare le configurazioni di progetto per le build di **debug** o **di rilascio,** scegliere quali progetti devono essere il progetto di avvio quando viene premuto **F5** e impostare le opzioni di analisi del codice.

## <a name="see-also"></a>Vedere anche

- [Soluzioni e progetti in Visual StudioSolutions and projects in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Gestire le proprietà di progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
