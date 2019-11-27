---
title: Disegnare forme e tracciati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8eb2d4f5b025be6f68860c18d1c14da017aaf3fe
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294320"
---
# <a name="draw-shapes-and-paths"></a>Disegnare forme e tracciati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella finestra di progettazione XAML una *forma* indica esattamente una forma. Ad esempio: un rettangolo, un cerchio o un'ellissi. Un *tracciato* è una versione più flessibile di una forma. È possibile ad esempio modificarne la forma o combinarli per creare nuove forme.

 Le forme e i tracciati usano la grafica vettoriale per una scalabilità ottima negli schermi ad alta risoluzione. Per altre informazioni sulla grafica vettoriale, guardare il video [What are Vector Graphics?](https://www.youtube.com/watch?v=MoCSwF0n-io) (Che cos'è la grafica vettoriale?) o leggere la definizione di [grafica vettoriale](https://www.webopedia.com/TERM/V/vector_graphics.html).

 **Contenuto dell'argomento:**

- [Disegnare una forma](#Shape)

- [Disegnare un tracciato](#Path)

- [Convertire una forma in un tracciato](#Convert)

- [Combinare tracciati](#Combine)

- [Creare un tracciato composto](#Compound)

- [Creare un tracciato di ritaglio](#Clipping)

## <a name="Shape"></a> Disegnare una forma
 Le forme sono disponibili nel pannello **Asset** .

 ![Categoria forme nel pannello Asset](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")

 Trascinare la forma da usare nella tavola da disegno. Usare quindi gli handle della forma per ridimensionarla, ruotarla, spostarla o inclinarla.

 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")

## <a name="Path"></a> Disegnare un tracciato
 Un tracciato è costituito da una serie di linee e curve collegate. Usare un tracciato per creare forme interessanti, non disponibili nel pannello **Asset** .

 È possibile disegnare un tracciato usando una riga, una penna o una matita. Questi strumenti sono disponibili nel pannello **Strumenti** .

 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")

### <a name="draw-a-straight-line"></a>Disegnare una linea retta
 Utilizzare lo strumento ![ ](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84Cf-a9bc8f38fc54")penna oppure lo strumento ![ ](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "linea eb618397-5283-48be-8396-3449be7b6fbf")linea.

 **Uso dello strumento penna**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84Cf-a9bc8f38fc54")

 Nella tavola da disegno fare clic una volta per definire il punto di inizio, quindi fare di nuovo clic per definire la fine della linea.

 **Uso dello strumento linea**![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "linea eb618397-5283-48be-8396-3449be7b6fbf")

 Nella tavola da disegno trascinare il puntatore dal punto in cui si vuole che abbia inizio la riga e quindi rilasciare il puntatore nel punto in cui si vuole che termini la linea.

### <a name="draw-a-curve"></a>Disegnare una curva
 Usare lo strumento ![ ](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84Cf-a9bc8f38fc54")penna.

 Nella tavola da disegno fare clic una volta per definire il punto di inizio di una linea, quindi fare clic e trascinare il puntatore per creare la curva desiderata.

 Per chiudere il tracciato, fare clic sul primo punto della linea.

### <a name="change-the-shape-of-a-curve"></a>Cambiare la forma di una curva
 Usare lo strumento ![ ](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-C116-451D-8dd2-1f88b8406362") **selezione diretta** .

 Fare clic sulla forma, quindi trascinare qualsiasi punto della forma per modificare le forme della curva.

### <a name="draw-a-free-form-path"></a>Disegnare un tracciato a mano libera
 Usare lo strumento ![ ](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd")matita.

 Nella tavola da disegno disegnare un tracciato a mano libera, proprio come se si usasse una vera matita.

### <a name="remove-part-of-a-path"></a>Eliminare una parte di un tracciato
 Usare lo strumento ![ ](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-C116-451D-8dd2-1f88b8406362") **selezione diretta** .

 Selezionare il tracciato contenente il segmento da eliminare, quindi fare clic su **Elimina** .

### <a name="remove-a-point-in-a-path"></a>Rimuovere un punto da un tracciato
 Usare lo strumento ![ ](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477E-4efa-a0f7-af20851e4daa")selezione e lo strumento ![ ](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84Cf-a9bc8f38fc54")penna.

 Usare lo strumento ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477E-4efa-a0f7-af20851e4daa") selezione per selezionare il percorso. Usare quindi lo ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84Cf-a9bc8f38fc54") strumento **penna** per fare clic sul punto che si vuole rimuovere.

### <a name="add-a-point-to-a-path"></a>Aggiungere un punto a un tracciato
 Usare lo strumento ![ ](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477E-4efa-a0f7-af20851e4daa")selezione e lo strumento ![ ](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84Cf-a9bc8f38fc54")penna.

 Usare lo strumento ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477E-4efa-a0f7-af20851e4daa") selezione per selezionare il percorso. Usare lo strumento ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84Cf-a9bc8f38fc54") penna per fare clic in un punto qualsiasi del percorso in cui si vuole aggiungere il punto.

## <a name="Convert"></a> Convertire una forma in un tracciato
 Per modificare una forma in modo analogo alla modifica di un tracciato, convertire la forma in tracciato.

 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with paths: Convert a shape to a path](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147) (Uso di tracciati: convertire una forma in un tracciato).

## <a name="Combine"></a> Combinare tracciati
 È possibile combinare forme e tracciati in un unico tracciato.

 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-a338-4ef4-96c5-dae51cc1ca8a")

|||||
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|Due forme prima della combinazione|![](../designers/media/b1-4.png "B1_4")|Interseca|
|![](../designers/media/b1-2.png "B1_2")|Unisci|![](../designers/media/b1-5.png "B1_5")|Escludi sovrapposizione|
|![](../designers/media/b1-3.png "B1_3")|Dividi|![](../designers/media/b1-6.png "B1_6")|Sottrai|

 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with paths: Combine paths](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195) (Uso di tracciati: combinare tracciati).

## <a name="Compound"></a> Creare un tracciato composto
 Quando si crea un tracciato composto, eventuali parti del tracciato che si intersecano vengono sottratte dal risultato e il tracciato risultante assume le proprietà visive del percorso situato più in basso.

 È possibile separare un tracciato composto in qualsiasi momento dopo averlo creato.

 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")

 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with paths: Create a compound path](https://www.youtube.com/watch?v=Io5bC0-nH6Q) (Uso di tracciati: creare un tracciato composto).

## <a name="Clipping"></a> Creare un tracciato di ritaglio
 Un tracciato di ritaglio è un tracciato o una forma applicato a un altro oggetto, in modo da nascondere le parti dell'oggetto mascherato esterne al tracciato di ritaglio.

 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")

 **Breve video:** ![Configurare le funzionalità installate](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Working with paths: Create a clipping path](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232) (Uso di tracciati: creare un tracciato di ritaglio).

## <a name="see-also"></a>Vedere anche
 [Creazione di un'interfaccia utente usando Blend per Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
