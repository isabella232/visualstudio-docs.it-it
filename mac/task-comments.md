---
title: Commenti dell'attività
description: Aggiunta di commenti dell'attività al codice
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 0e2aedf52974529864650fabe6d83db2a60b50cd15156e0cc2e96583261de3ed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349290"
---
# <a name="task-comments"></a>Commenti dell'attività

Quando si scrive codice, è prassi standard commentare esplicitamente il codice incompleto o dubbio o le soluzioni rapide con avvisi. I token di segnalazione predefiniti forniti da Visual Studio per Mac sono TODO, HACK, FIXME e UNDONE. È possibile definire token personalizzati in **Visual Studio > Preferenze > Ambiente > Attività**, come illustrato nell'immagine seguente:

![Preferenze dell'elenco attività](media/source-editor-image10.png)

Quando si aggiunge un nuovo commento di attività, includere la parola chiave dell'attività. Esempio:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio per Mac attenzione a questi marcatori evidenziandoli nella finestra  Elenco attività, che può essere visualizzata usando il menu **Visualizza** > attività:

![Finestra Elenco attività che mostra un singolo elemento TODO](media/source-editor-image11.png)

## <a name="see-also"></a>Vedi anche

- [Usare l'elenco attività (Visual Studio in Windows)](/visualstudio/ide/using-the-task-list)