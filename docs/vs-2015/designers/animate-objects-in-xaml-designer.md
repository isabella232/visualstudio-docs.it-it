---
title: Animare oggetti in una finestra di progettazione XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ea2fdf1f47385a9be26fa65a93b9104b2d864079
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658014"
---
# <a name="animate-objects-in-xaml-designer"></a>Animare oggetti in una finestra di progettazione XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare brevi animazioni per spostare gli oggetti o per applicare agli oggetti la dissolvenza in entrata e in uscita.

 Per iniziare, creare uno *storyboard*. Uno storyboard contiene uno o più *sequenze temporali*. Impostare i *fotogrammi chiave* in una sequenza temporale per contrassegnare le modifiche alle proprietà. Quando poi si esegue l'animazione, Blend interpola le modifiche alle proprietà nel periodo di tempo indicato, garantendo in tal modo una transizione graduale. È possibile aggiungere un'animazione a qualsiasi proprietà che appartiene a un oggetto, anche quelle non visive.

 La figura seguente mostra uno storyboard denominato **MoveUp**. La sequenza temporale contiene fotogrammi chiave che indicano le posizioni X e Y di un rettangolo. Quando si esegue questa animazione, il rettangolo si sposta da una posizione a un altro in modo graduale.

 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")

 Per imparare a creare animazioni, è possibile guardare i video seguenti.

|Breve video:|Procedure incluse:|
|--------------------------|-------------------|
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [creare sequenze temporali](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Creare una sequenza temporale e usare gli oggetti nella sequenza temporale.|
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [aggiungere fotogrammi chiave e ripetere l'animazione](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Aggiungere fotogrammi chiave e impostare le proprietà di ogni fotogramma. Eseguire quindi l'animazione e notare la transizione graduale applicata agli oggetti.|
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [aggiungere trigger di evento per l'interattività](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Avviare un'animazione quando si verifica un evento, ad esempio quando viene caricata la finestra.|
|![Configura funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [animazione colori](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Per modificare il colore di un oggetto, usare un'animazione.|
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [creare e modificare i percorsi di movimento](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animare oggetti lungo un percorso.|
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [semplifica la semplicità di fotogrammi chiave](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Velocizzare o rallentare un'animazione nella parte iniziale (*interpolazione con variazione in entrata*) o nella parte finale (*interpolazione con variazione in uscita*) di un'animazione.|
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [aggiungere un'animazione al pulsante](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Creare effetti interessanti visualizzati su un pulsante quando viene selezionato dall'utente.|
|![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [creare un'animazione e usare l'interpolazione](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Aggiungere un'animazione agli effetti visualizzati quando un utente fa clic su un pulsante nell'immagine di una calcolatrice.|

## <a name="see-also"></a>Vedere anche
 [Creazione di un'interfaccia utente usando Blend per Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
