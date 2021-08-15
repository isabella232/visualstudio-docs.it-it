---
title: Commenti dell'attività
description: Aggiunta di commenti dell'attività al codice
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 6966a83ececf747271e2135508864de0be1a77a81eff584cab64dcde52c75f24
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121439627"
---
# <a name="task-comments"></a>Commenti dell'attività

Quando si scrive codice, è prassi standard commentare esplicitamente il codice incompleto o dubbio o le soluzioni rapide con avvisi. I token di segnalazione predefiniti forniti da Visual Studio per Mac sono TODO, HACK, FIXME e UNDONE. È possibile definire token personalizzati in **Visual Studio > Preferenze > Ambiente > Attività**, come illustrato nell'immagine seguente:

![Preferenze dell'elenco attività](media/source-editor-image10.png)

Quando si aggiunge un nuovo commento di attività, includere la parola chiave dell'attività. Esempio:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio per Mac attira l'attenzione su questi marcatori evidenziandoli nel riquadro **Elenco attività**, visualizzato spostandosi su **Visualizza > Riquadri > Attività**:

![Riquadro Elenco attività](media/source-editor-image11.png)

## <a name="see-also"></a>Vedi anche

- [Usare l'elenco attività (Visual Studio in Windows)](/visualstudio/ide/using-the-task-list)