---
title: Organizzare gli oggetti in contenitori di layout
description: Informazioni sui pannelli e i controlli di layout in finestra di progettazione XAML usati per disporre gli oggetti in una pagina, ad esempio Grid, Canvas, Border e Viewbox.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: e3a08c647f115d6f01ecc8543e5b87d1d4a15a8bf0e20f9633c2999eac41d63c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267234"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizzare gli oggetti in contenitori nella finestra di progettazione XAML

Questo articolo descrive i pannelli di layout e i controlli della finestra di progettazione XAML.

Si supponga di voler impostare la posizione degli oggetti, come immagini, pulsanti e video, in una pagina. È probabile che si preferisca organizzarli in righe e colonne, su un'unica riga disposti orizzontalmente o verticalmente o impostare per ognuno una posizione fissa.

Dopo aver dedicato tempo all'organizzazione degli oggetti nella pagina, è possibile passare alla scelta di un pannello di layout. Inizialmente in tutte le pagine è presente un pannello di layout in quanto viene usato per aggiungervi gli oggetti. Il pannello di layout predefinito è di tipo **Grid**, ma è possibile modificarlo.

I pannelli di layout non vengono però usati unicamente per organizzare gli oggetti in una pagina, ma anche per progettare tenendo conto di risoluzioni e dimensioni dello schermo diverse. Quando gli utenti eseguono l'app, tutti gli elementi presenti in un pannello di layout vengono ridimensionati in base all'area dello schermo del dispositivo. Ovviamente, se si preferisce che gli elementi non vengano ridimensionati, è possibile disattivare questo comportamento per una parte o per l'intero layout, usando a tale scopo le proprietà height e width.

## <a name="layout-panels"></a>Pannelli di layout

Per definire inizialmente la pagina, scegliere uno dei seguenti pannelli di layout. La pagina può comunque contenere più pannelli di layout. Si può infatti iniziare con un pannello di layout di tipo **Grid** e quindi aggiungerne uno di tipo **StackPanel** a un'area del pannello **Grid** in modo da disporre i controlli verticalmente in tale elemento.

I seguenti pannelli di layout sono quelli più usati, ma ne esistono altri. Tutti i pannelli sono disponibili nella **casella degli strumenti** in Visual Studio o nel pannello **Asset** in Blend per Visual Studio.

### <a name="grid"></a>Pannello Grid

Consente di disporre gli oggetti in righe e colonne.

![Pannello di layout della griglia](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Consente di disporre gli oggetti in aree della griglia uguali o uniformi. Questo pannello è molto utile per definire la disposizione di un elenco di immagini.

(Disponibile solo per i progetti WPF)

![Pannello di layout di tipo UniformGrid](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

### <a name="canvas"></a>Canvas

Consente di disporre gli oggetti nel modo desiderato. Quando gli utenti eseguono l'app, a questi elementi verranno assegnate posizioni fisse sullo schermo.

![Pannello di layout del canvas](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Consente di disporre gli oggetti su un'unica riga orizzontalmente o verticalmente.

![Pannello di layout StackPanel](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Consente di disporre gli oggetti in modo sequenziale da sinistra verso destra. Quando il pannello esaurisce lo spazio all'estremità destra, *esegue il wrapping* del contenuto sulla riga successiva e così via da sinistra verso destra e dall'alto verso il basso. È anche possibile impostare per un pannello di questo tipo l'orientamento verticale in modo che gli oggetti vengano spostati dall'alto verso il basso e da sinistra verso destra.

(Disponibile solo per i progetti WPF)

![Pannello di layout WrapPanel](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

È anche possibile disporre gli oggetti in modo che rimangano *ancorati* a un bordo del pannello.

(Disponibile solo per i progetti WPF)

![Pannello di layout DockPanel](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Guardare un breve video:** ![ Pulsante Di ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [riproduzione WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Controlli di layout

È possibile aggiungere oggetti anche ai controlli di layout, che pur includendo un minor numero di funzionalità rispetto a un pannello di layout, possono risultare utili per determinati scenari.

I seguenti controlli di layout sono quelli più diffusi, ma ne esistono altri. Tutti i pannelli sono disponibili nella **casella degli strumenti** in Visual Studio o nel pannello **Asset** in Blend per Visual Studio.

### <a name="border"></a>Bordo

Consente di creare un bordo, uno sfondo o entrambi intorno a un oggetto. È possibile aggiungere un solo oggetto a un controllo **Border**. Per applicare un bordo o uno sfondo a più oggetti, aggiungere a **Border** un pannello di layout, quindi aggiungere gli oggetti al pannello o al controllo.

![Controllo di layout di bordo](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Popup

Consente di visualizzare informazioni o opzioni destinate agli utenti in una finestra. È possibile aggiungere un solo oggetto a un controllo **Popup**. Per impostazione predefinita, un controllo **Popup** contiene un pannello di layout **Grid**, ma è possibile cambiare questa impostazione.

### <a name="scrollviewer"></a>ScrollViewer

Consente agli utenti di scorrere verso il basso in una pagina o un'area di una pagina. Dal momento che è possibile aggiungere un solo oggetto a un controllo **ScrollViewer**, è preferibile aggiungere un pannello di layout, come **Grid** o **StackPanel**.

![Controllo di layout ScrollViewer](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

Consente di ridimensionare gli oggetti come con un controllo zoom. È possibile aggiungere un solo oggetto a un controllo **Viewbox**. Se si vuole applicare questo effetto a più oggetti, aggiungere un pannello di layout a **ViewBox** e quindi aggiungere i controlli a tale pannello.

![Controllo di layout ViewBox](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Vedi anche

- [Usare gli elementi nella finestra di progettazione XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Creare un'interfaccia utente tramite la finestra di progettazione XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
