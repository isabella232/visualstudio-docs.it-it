---
title: 'Procedura: visualizzare i tipi esistenti (Progettazione classi)'
description: Informazioni su come visualizzare un tipo esistente e i relativi membri aggiungendone la forma a un diagramma classi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 03bd0d6bc66e97c0449287823457c3af8eb0cc86
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109474"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Procedura: Visualizzare i tipi esistenti in Progettazione classi

Per visualizzare un tipo esistente con i relativi membri, aggiungere la forma a un diagramma classi.

È possibile vedere tipi locali e tipi a cui viene fatto riferimento. Un tipo locale è presente nel progetto aperto ed è in lettura/scrittura. Un tipo a cui viene fatto riferimento esiste in un altro progetto o in un assembly a cui viene fatto riferimento ed è in sola lettura.

Per progettare nuovi tipi nei diagrammi classi, [vedere Procedura: Creare tipi usando Progettazione classi](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Per vedere i tipi di un progetto in un diagramma di classi

1. Da un progetto in **Esplora soluzioni** aprire un file di diagramma classi (con estensione cd) esistente. In alternativa, se non sono disponibili diagrammi classi, aggiungerne uno nuovo al progetto. Vedere [Procedura: Aggiungere diagrammi classi ai progetti](how-to-add-class-diagrams-to-projects.md).

2. Dal progetto **in** Esplora soluzioni trascinare un file di codice sorgente nel diagramma classi.

    > [!NOTE]
    > Se la soluzione contiene un progetto che condivide il codice con più app, è possibile trascinare file o codice in un diagramma classi solo da queste origini:
    >
    > - Il progetto di app contenente il diagramma
    > - Un progetto condiviso importato dal progetto di app
    > - Un progetto a cui si fa riferimento
    > - Un assembly

    Le forme che rappresentano i tipi definiti nel file di codice sorgente appariranno nel diagramma nella posizione in cui è stato trascinato il file.

È anche possibile visualizzare i tipi nel progetto trascinando uno o più tipi dal nodo del progetto in **Visualizzazione classi** al diagramma classi.

> [!TIP]
> Se **Visualizzazione classi** non è aperto, aprire **Visualizzazione classi** **dal** menu Visualizza.

Per visualizzare i tipi nelle posizioni predefinite del **diagramma,** selezionare uno o più tipi in Visualizzazione classi , fare clic con il pulsante destro del mouse sui tipi selezionati e scegliere **Visualizza diagramma classi**.

> [!NOTE]
> Se nel progetto esiste già un diagramma classi chiuso contenente il tipo, tale diagramma verrà aperto per visualizzare la forma del tipo. Tuttavia, se nel progetto non esiste alcun diagramma classi contenente il **tipo, Progettazione classi** crea un nuovo diagramma classi nel progetto e lo apre per visualizzare il tipo.

La prima volta che viene visualizzato un tipo nel diagramma, la relativa forma appare compressa per impostazione predefinita. È possibile espanderla per visualizzarne il contenuto.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Per visualizzare il contenuto di un progetto in un diagramma classi

In **Esplora soluzioni** o **Visualizzazione classi** fare clic con il pulsante destro del mouse sul progetto e scegliere Visualizza **,** quindi scegliere Visualizza **diagramma classi.** Verrà creato un diagramma classi compilato automaticamente.

## <a name="see-also"></a>Vedi anche

- [Procedura: Visualizzare l'ereditarietà tra tipi](how-to-view-inheritance-between-types.md)
- [Procedura: Personalizzare i diagrammi classi](how-to-customize-class-diagrams.md)
- [Visualizzazione di tipi e relazioni](designing-and-viewing-classes-and-types.md)
