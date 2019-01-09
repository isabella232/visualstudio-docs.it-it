---
title: Gestire le proprietà di progetti e soluzioni
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f1ae5ae9b0bd751deca5e26ac4ea09e884e5db0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824301"
---
# <a name="manage-project-and-solution-properties"></a>Gestire le proprietà di progetti e soluzioni

Le proprietà dei progetti governano molti aspetti della compilazione, del debug, del test e della distribuzione. Alcune proprietà sono comuni tra tutti i tipi di progetto e altre sono univoche di piattaforme o linguaggi specifici. Per accedere alle proprietà del progetto, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà** oppure digitare "proprietà" nella casella di ricerca **Avvio veloce** nella barra dei menu.

![Menu di scelta rapida Progetto](../ide/media/vs2015_proj_prop_menu.gif)

I progetti .NET potrebbero anche avere un nodo di proprietà nell'albero del progetto.

![Nodo Proprietà nell'albero Esplora soluzioni](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Gestire le proprietà di progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Proprietà di progetti

Le proprietà del progetto sono organizzate in gruppi e ogni gruppo ha una propria pagina delle proprietà. Le pagine possono essere diverse a seconda del linguaggio e del tipo di progetto.

### <a name="c-visual-basic-and-f-projects"></a>Progetti C#, Visual Basic e F#

Nei progetti C#, Visual Basic e F# le proprietà sono esposte in **Progettazione progetti**. La figura seguente mostra la pagina delle proprietà di **compilazione** per un progetto WPF in C#:

![Progettazione progetti di Visual Studio](../ide/media/vs2015_proppage_build.png)

Per informazioni su ognuna delle pagine delle proprietà in **Creazione progetti**, vedere [Riferimenti alle proprietà di progetto](../ide/reference/project-properties-reference.md).

> [!TIP]
> Le soluzioni, così come gli elementi del progetto, hanno alcune proprietà, che sono accessibili nella [Finestra Proprietà](../ide/reference/properties-window.md), non in **Creazione progetti**.

### <a name="c-and-javascript-projects"></a>Progetti C++ e JavaScript

I progetti C++ e JavaScript hanno un'interfaccia utente differente per la gestione delle proprietà del progetto. Questa illustrazione mostra la pagina delle proprietà di un progetto C++ (le pagine JavaScript sono simili):

![Proprietà dei progetti Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png)

Per informazioni sulle proprietà di progetto C++, vedere [Utilizzo di proprietà di progetto (C++)](/cpp/ide/working-with-project-properties). Per altre informazioni sulle proprietà JavaScript, vedere [Pagine proprietà, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Proprietà della soluzione

Per accedere alle proprietà della soluzione, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Proprietà**. Nella finestra di dialogo è possibile impostare le configurazioni di progetto per le compilazioni di **debug** o di **rilascio**, scegliere i progetti che devono essere il progetto di avvio quando si preme **F5** e impostare le opzioni di analisi del codice.

## <a name="see-also"></a>Vedere anche

- [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Gestire le proprietà di progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
