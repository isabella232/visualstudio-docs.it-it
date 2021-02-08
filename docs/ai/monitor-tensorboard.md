---
title: Monitorare con TensorBoard
description: Informazioni su come usare Visual Studio per visualizzare lo stato di avanzamento del training del modello con TensorBoard.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: edb6fe17902ad84ec6d7a6e5b9929bd965e7c29b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841393"
---
# <a name="monitor-with-tensorboard"></a>Monitorare con TensorBoard

È possibile visualizzare lo stato del training del modello con TensorBoard.

1. Fare clic con il pulsante destro de mouse sul progetto e scegliere **Run TensorBoard** (Esegui TensorBoard) quindi selezionare la directory dei log di output di TensorBoard.

    ![Screenshot di Visual Studio Esplora soluzioni con il progetto MNIST selezionato. Viene aperto un menu di scelta rapida e viene selezionato il comando Esegui TensorBoard.](media/monitor-tensorboard/run-tensorboard.png)

2. Si noti che gli errori diminuiscono nel tempo e ciò indica un miglioramento della qualità.

    ![Screenshot della finestra principale di TensorBoard che mostra le visualizzazioni grafiche dei dati dei log TensorBoard.](media/monitor-tensorboard/tensorboard.png)
