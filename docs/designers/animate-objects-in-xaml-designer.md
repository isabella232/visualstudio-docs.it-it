---
title: Animare oggetti in una finestra di progettazione XAML
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: f6fbeceeb0c9943e561c5bd4e353551005be23a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960204"
---
# <a name="animate-objects-in-xaml-designer"></a>Animare oggetti in una finestra di progettazione XAML

È possibile creare brevi animazioni per spostare gli oggetti o per applicare agli oggetti la dissolvenza in entrata e in uscita.

Per iniziare, creare uno *storyboard*. Uno storyboard contiene uno o più *sequenze temporali*. Impostare i *fotogrammi chiave* in una sequenza temporale per contrassegnare le modifiche alle proprietà. Quando poi si esegue l'animazione, Blend interpola le modifiche alle proprietà nel periodo di tempo indicato, garantendo in tal modo una transizione graduale. È possibile aggiungere un'animazione a qualsiasi proprietà che appartiene a un oggetto, anche quelle non visive.

La figura seguente mostra uno storyboard denominato **MoveUp**. La sequenza temporale contiene fotogrammi chiave che indicano le posizioni X e Y di un rettangolo. Quando si esegue questa animazione, il rettangolo si sposta da una posizione a un altro in modo graduale.

![Storyboard MoveUp nella finestra di progettazione XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Vedere anche

- [Creare un'interfaccia utente usando Blend per Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)