---
title: Gestire le proprietà di progetti e soluzioni
description: Informazioni su come gestire sia le proprietà del progetto che le proprietà della soluzione in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/01/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: fa70c86c768ed37150e70454c12c5889aa820523
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398429"
---
# <a name="manage-project-and-solution-properties"></a>Gestire le proprietà di progetti e soluzioni

Le proprietà dei progetti governano molti aspetti della compilazione, del debug, del test e della distribuzione. Alcune proprietà sono comuni tra tutti i tipi di progetto e altre sono univoche di piattaforme o linguaggi specifici.

> [!TIP]
> In [Visual Studio 2022 Preview](/visualstudio/releases/2022/release-notes-preview)sono state aggiunte nuove funzionalità alle proprietà del progetto e ne è stata aggiornata l'interfaccia utente. Per altre informazioni, vedere il post di blog [**Revamped Project Properties UI**](https://devblogs.microsoft.com/visualstudio/flexible-theming-visual-studio/) (Interfaccia utente delle proprietà di Project rinnovata).

Per accedere alle proprietà del **progetto,** fare clic con il pulsante  destro del mouse sul nodo  del progetto in Esplora soluzioni e scegliere Proprietà oppure digitare le proprietà nella casella di ricerca sulla barra dei menu e scegliere Finestra Proprietà dai risultati. 

![Menu di scelta rapida del progetto](../ide/media/vs2015_proj_prop_menu.gif)

I progetti .NET potrebbero anche avere un nodo di proprietà nell'albero del progetto.

![Nodo Proprietà nell'albero Esplora soluzioni](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Gestire le proprietà di progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Proprietà progetto

Le proprietà del progetto sono organizzate in gruppi e ogni gruppo ha una propria pagina delle proprietà. Le pagine possono essere diverse a seconda del linguaggio e del tipo di progetto.

### <a name="c-visual-basic-and-f-projects"></a>Progetti C#, Visual Basic e F#

Nei progetti C#, Visual Basic e F#, le proprietà vengono esposte in **progettazione Project .** La figura seguente mostra la **pagina delle** proprietà Compila per un progetto WPF in C#:

![Progettazione progetti di Visual Studio](../ide/media/vs2015_proppage_build.png)

Per informazioni su ognuna delle pagine delle proprietà in **Progettazione Project**, Project informazioni di riferimento [sulle proprietà](../ide/reference/project-properties-reference.md).

> [!TIP]
> Le soluzioni hanno alcune proprietà, così come gli elementi di progetto. Queste proprietà sono accessibili nella finestra [Finestra Proprietà](../ide/reference/properties-window.md), non **Project Progettazione**.

### <a name="c-and-javascript-projects"></a>Progetti C++ e JavaScript

I progetti C++ e JavaScript hanno un'interfaccia utente differente per la gestione delle proprietà del progetto. Questa illustrazione mostra la pagina delle proprietà di un progetto C++ (le pagine JavaScript sono simili):

![Proprietà dei progetti Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png)

Per informazioni sulle proprietà di progetto C++, vedere [Utilizzo di proprietà di progetto (C++)](/cpp/build/working-with-project-properties). Per altre informazioni sulle proprietà JavaScript, vedere [Pagine delle proprietà, JavaScript.](../ide/reference/property-pages-javascript.md)

## <a name="solution-properties"></a>Proprietà della soluzione

Per accedere alle proprietà della soluzione, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Proprietà**. Nella finestra di dialogo è  possibile impostare le configurazioni di progetto per le **build** di debug o di rilascio, scegliere quali progetti devono essere il progetto di avvio quando si preme **F5** e impostare le opzioni di analisi del codice.

## <a name="see-also"></a>Vedi anche

- [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Gestire le proprietà di progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
