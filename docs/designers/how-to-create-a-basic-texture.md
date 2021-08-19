---
title: 'Procedura: Creare una trama di base'
description: Informazioni su come usare l'editor di immagini per creare una trama di base, tra cui l'impostazione delle dimensioni della trama, l'impostazione delle proprietà dello strumento e altre attività.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: bd312e8934d14a986606020558adc57339250706
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112061"
---
# <a name="how-to-create-a-basic-texture"></a>Procedura: Creare una trama di base

Questo articolo illustra come usare l'editor di immagini per creare una trama di base, incluse le attività seguenti:

- Impostazione della dimensione della trama

- Impostazione dei colori di primo piano e di sfondo

- Utilizzo del canale alfa (trasparenza)

- Utilizzo degli strumenti **Riempimento** e **Ellisse**

- Impostazione delle proprietà dello strumento

## <a name="create-a-basic-texture"></a>Creare una trama di base

È possibile usare l'editor di immagini per creare e modificare immagini e trame per un gioco o un'app.

La procedura seguente illustra come creare una trama che rappresenta una destinazione "bullseye". Al termine dell'operazione, la trama dovrebbe essere simile all'immagine seguente. Per illustrare meglio la trasparenza nella trama, l'editor di immagini è stato configurato per l'utilizzo di un modello verde a scacchi.

![Destinazione "Bullseye" con trasparenza visualizzata in verde](../designers/media/digit-bullseye-texture-in-editor.png)

Prima di iniziare, assicurarsi che sia visualizzata la finestra **Proprietà**. Usare la finestra **Proprietà** per impostare la dimensione dell'immagine, modificare le proprietà dello strumento e specificare i colori mentre si lavora.

### <a name="create-a-bullseye-target-texture"></a>Creare una trama di destinazione "bersaglio"

1. Creare una trama da usare. Per informazioni su come aggiungere una trama al progetto, vedere [Editor di immagini](../designers/image-editor.md#get-started).

2. Impostare le dimensioni dell'immagine su 512 x 512 pixel. Nella finestra **Proprietà** impostare il valore delle proprietà **Larghezza** e **Altezza** su `512`.

3. Nella barra degli strumenti scegliere lo strumento **Riempimento**. Nella finestra **Proprietà** vengono visualizzate le proprietà dello strumento **Riempimento** insieme alle proprietà dell'immagine.

4. Impostare il colore di primo piano su un nero completamente trasparente. Nella finestra **Proprietà**, nel gruppo di proprietà **Colori**, selezionare **Primo piano**. Impostare i valori delle proprietà **R**, **G**, **B** e **A** accanto alla selezione colori su `0`.

5. Sulla barra degli strumenti  dell'editor di immagini scegliere lo strumento Riempimento, quindi tenere premuto **MAIUSC** e scegliere un punto qualsiasi nell'immagine. **L'uso del** tasto MAIUSC fa sì che il valore alfa del colore di riempimento sostituisca il colore nell'immagine; In caso contrario, il valore alfa viene usato per unire il colore di riempimento con il colore nell'immagine.

    > [!IMPORTANT]
    > Questo passaggio, insieme alla selezione del colore nel passaggio precedente, assicura che l'immagine di base sia preparata per la trama di destinazione "bullseye" che si intende disegnare. Poiché l'immagine viene riempita con un nero trasparente e il bordo della destinazione è nero, non saranno presenti artefatti di aliasing intorno alla destinazione.

6. Nella barra degli strumenti scegliere lo strumento **Ellissi**.

7. Impostare il colore di primo piano su un nero completamente opaco. Impostare i valori delle proprietà **R**, **G** e **B** su `0` e il valore della proprietà **A** su `255`.

8. Impostare il colore di sfondo su un bianco completamente opaco. Nella finestra **Proprietà**, nel gruppo di proprietà **Colori**, selezionare **Sfondo**. Impostare i valori delle proprietà **R**, **G**, **B** e **A** su `255`.

9. Impostare la larghezza del contorno dell'ellisse. Nella finestra **Proprietà**, nel gruppo di proprietà **Aspetto**, impostare il valore della proprietà **Larghezza** su `8`.

10. Assicurarsi che l'antialiasing sia abilitato. Nella finestra **Proprietà**, nel gruppo di proprietà **Aspetto**, assicurarsi che la proprietà **Anti-alias** sia impostata.

11. Usando lo strumento **Ellisse** disegnare un cerchio dalla coordinata in pixel `(3, 3)` alla coordinata in pixel `(508, 508)`. Per disegnare più facilmente il cerchio, è possibile tenere premuto **MAIUSC** mentre si disegna.

    > [!NOTE]
    > Le coordinate in pixel della posizione corrente del puntatore sono visualizzate nella barra di stato di Visual Studio.

12. Modificare il colore di sfondo. Impostare **R** su `44`, **G** su `165`, **B** su `211` e **A** su `255`.

13. Disegnare un altro cerchio dalla coordinata in pixel `(64, 64)` alla coordinata in pixel `(448, 448)`.

14. Impostare di nuovo il colore di sfondo su un bianco completamente opaco. Impostare **R**, **G**, **B** e **A** su `255`.

15. Disegnare un altro cerchio dalla coordinata in pixel `(128, 128)` alla coordinata in pixel `(384, 384)`.

16. Modificare il colore di sfondo. Impostare **R** su `255`, **G** e **B** su `64` e **A** su `255`.

17. Disegnare un altro cerchio dalla coordinata in pixel `(192, 192)` alla coordinata in pixel `(320, 320)`.

La trama di destinazione "bullseye" è completa. Di seguito è riportata l'immagine finale, illustrata con la trasparenza.

![Trama di destinazione "bullseye" completa](../designers/media/gfx_image_demo_bullseye.png)

Come passaggio successivo è possibile generare i livelli MIP per la trama. Per informazioni, vedere [Procedura: Creare e modificare livelli MIP.](../designers/how-to-create-and-modify-mip-levels.md)

## <a name="see-also"></a>Vedi anche

- [Editor di immagini](../designers/image-editor.md)
