---
title: Commenti dell'attività
description: Aggiunta di commenti dell'attività al codice
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67692319"
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