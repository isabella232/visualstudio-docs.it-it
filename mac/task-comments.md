---
title: Commenti dell'attività
description: Aggiunta di commenti dell'attività al codice
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294279"
---
# <a name="task-comments"></a>Commenti dell'attività

Quando si scrive codice, è prassi standard commentare esplicitamente il codice incompleto o dubbio o le soluzioni rapide con avvisi. I token di segnalazione predefiniti forniti da Visual Studio per Mac sono TODO, HACK, FIXME e UNDONE. È possibile definire token personalizzati in **Visual Studio > Preferenze > Ambiente > Attività**, come illustrato nell'immagine seguente:

![Preferenze dell'elenco attività](media/source-editor-image10.png)

Quando si aggiunge un nuovo commento di attività, includere la parola chiave dell'attività. Ad esempio:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio per Mac attira l'attenzione su questi marcatori evidenziandoli nel riquadro **Elenco attività**, visualizzato spostandosi su **Visualizza > Riquadri > Attività**:

![Riquadro Elenco attività](media/source-editor-image11.png)

## <a name="see-also"></a>Vedere anche

- [Usare l'elenco attività (Visual Studio in Windows)](/visualstudio/ide/using-the-task-list)