---
title: Commenti dell'attività
description: Aggiunta di commenti dell'attività al codice
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 44d82becfbf3a16ccd2158ac05e171e8530cd721
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224173"
---
# <a name="task-comments"></a>Commenti dell'attività

Quando si scrive codice, è prassi standard commentare esplicitamente il codice incompleto o dubbio o le soluzioni rapide con avvisi. I token di segnalazione predefiniti forniti da Visual Studio per Mac sono TODO, HACK, FIXME e UNDONE. È possibile definire token personalizzati in **Visual Studio > Preferenze > Ambiente > Attività**, come illustrato nell'immagine seguente:

 ![Preferenze dell'elenco attività](media/source-editor-image10.png)

Quando si aggiunge un nuovo commento di attività, includere la parola chiave dell'attività. Ad esempio:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio per Mac attira l'attenzione su questi marcatori evidenziandoli nel riquadro Elenco attività, visualizzato spostandosi su **Visualizza > Riquadri > Attività**:

![Riquadro Elenco attività](media/source-editor-image11.png)