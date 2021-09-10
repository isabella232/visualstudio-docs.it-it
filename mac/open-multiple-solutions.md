---
title: 'Procedura: Aprire più soluzioni'
description: Informazioni su come aprire più soluzioni in Visual Studio per Mac e su come aprire più istanze dell'applicazione.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: e54f002141379d93a40df69ea070d5a64eba2f7d
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964650"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Aprire più soluzioni o istanze di Visual Studio per Mac

Per impostazione predefinita, tutte le applicazioni in un Mac, incluso Visual Studio per Mac, sono app _a istanza singola_. Ciò significa che se l'applicazione che si vuole usare è già aperta (come indicato da un "punto" sotto l'icona nel Dock) e si seleziona di nuovo l'icona, viene aperta l'istanza in esecuzione, anziché una nuova. Se sono necessarie altre istanze dell'applicazione, è possibile richiedere al sistema di aprirle, come descritto nella [sezione successiva](#open-a-second-instance-of-visual-studio-for-mac).

Quando si apre una soluzione, poi, il comportamento predefinito corrisponde all'apertura della soluzione in una nuova area di lavoro e alla chiusura dell'area di lavoro corrente (se necessario). È possibile sostituire questo comportamento predefinito, mantenendo aperta l'area di lavoro corrente, come descritto nella sezione [Aprire una seconda soluzione](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Aprire una seconda istanza di Visual Studio per Mac

Per aprire una seconda istanza dell'ambiente di sviluppo integrato (IDE), fare clic con il pulsante destro del mouse sull'icona di Visual Studio nell'ancoraggio o nella cartella **Applicazioni** e selezionare **Nuova istanza**.

![Screenshot dell'opzione di menu Nuova istanza nell'icona di Visual Studio selezionata con il pulsante destro del mouse](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>Aprire una seconda soluzione all'interno di un'istanza singola

Per aprire una seconda soluzione insieme alla prima, procedere come segue:

1. Con la prima soluzione già aperta, selezionare **Apri**  >  **file.**
2. Sfogliare il file system per individuare la soluzione esistente.
3. Selezionare il file con estensione **sln** e quindi **Opzioni**:

    ![Screenshot di Visual Studio per Mac, con il file con estensione sln e il comando Opzioni evidenziati](media/open-multiple-solutions-image3.png)

4. Deselezionare la casella **Chiudi l'area di lavoro corrente**:

    ![Screenshot della finestra di dialogo Opzioni con la casella Chiudi l'area di lavoro corrente deselezionata](media/open-multiple-solutions-image1.png)

5. Selezionare **Apri** per aprire la seconda soluzione nella finestra della soluzione.

In alternativa, se la soluzione è stata aperta di recente, è possibile usare la procedura seguente:

1. Passare a **File**  >  **Recent Solutions (File soluzioni recenti).**

    ![Screenshot del menu Soluzioni recenti](media/open-multiple-solutions-image2.png)

1. Tenere premuto **Ctrl** e selezionare la soluzione. Questa combinazione apre la seconda soluzione nella finestra della soluzione.

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
