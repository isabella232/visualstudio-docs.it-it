---
title: Monitorare con TensorBoard
description: Informazioni su come usare i Visual Studio per visualizzare lo stato di avanzamento del training del modello con TensorBoard.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: d5d4fb9799a94e6c583c8f49ccf69f284834a448
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633331"
---
# <a name="monitor-with-tensorboard"></a>Monitorare con TensorBoard

È possibile visualizzare lo stato del training del modello con TensorBoard.

1. Fare clic con il pulsante destro de mouse sul progetto e scegliere **Run TensorBoard** (Esegui TensorBoard) quindi selezionare la directory dei log di output di TensorBoard.

    ![Screenshot della Visual Studio Esplora soluzioni con il progetto MNIST selezionato. È aperto un menu di scelta rapida ed è selezionato il comando Esegui TensorBoard.](media/monitor-tensorboard/run-tensorboard.png)

2. Si noti che gli errori diminuiscono nel tempo e ciò indica un miglioramento della qualità.

    ![Screenshot della finestra principale di TensorBoard che mostra visualizzazioni grafiche dei dati dai log di TensorBoard.](media/monitor-tensorboard/tensorboard.png)
