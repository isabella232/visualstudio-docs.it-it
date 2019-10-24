---
title: Eseguire il training di un modello TensorFlow in locale
description: Eseguire un modello TensorFlow in locale in Visual Studio Tools for AI
keywords: ai, visual studio, tensorflow, locale
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 43ce126baeb96efcaab3c40bac912274ee1cd8c7
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777436"
---
# <a name="train-a-tensorflow-model-locally"></a>Eseguire il training di un modello TensorFlow in locale

Questa guida introduttiva descrive come eseguire il training di un modello TensorFlow con il set di dati [MNIST](http://yann.lecun.com/exdb/mnist/) in locale in Visual Studio Tools for AI.

Il database MNIST include un set di training di 60.000 esempi e un set di test di 10.000 esempi di cifre scritte a mano.

## <a name="prerequisites"></a>Prerequisites

Prima di iniziare, assicurarsi di aver installato quanto segue:

### <a name="google-tensorflow"></a>Google TensorFlow

Eseguire il comando seguente in un terminale:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy e SciPy
Installare [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) e [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Scaricare il codice di esempio
Scaricare questo [repository di GitHub](https://github.com/Microsoft/samples-for-ai) contenente esempi per iniziare ad approfondire TensorFlow, CNTK, Theano e altro.

## <a name="open-solution-and-train-model"></a>Aprire la soluzione ed eseguirne il training del modello

- Avviare Visual Studio e selezionare **File > Apri > Progetto/Soluzione**.

- Selezionare la cartella **TensorflowExamples** dal repository degli esempi scaricato e aprire il file **TensorflowExamples.sln**.

   ![Apertura del progetto](media/tensorflow-local/open-project.png)

   ![Apertura della soluzione](media/tensorflow-local/open-solution.png)

- Trovare il progetto MNIST in **Esplora soluzioni**, fare clic con il pulsante destro del mouse e scegliere **Imposta come progetto di avvio**.

- Fare clic su **Avvia**.

- L'output viene stampato nella console.

   ![Output di esempio dalla console](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Eseguire il training di un modello TensorFlow nel cloud](tensorflow-vm.md)
