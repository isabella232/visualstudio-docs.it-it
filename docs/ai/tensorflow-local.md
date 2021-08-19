---
title: Eseguire il training di un modello TensorFlow in locale
description: Eseguire un modello TensorFlow in locale in Visual Studio Tools for AI
keywords: ai, visual studio, tensorflow, locale
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: d1e27999af1c467f0231c28a6f1ea53fb4c466a6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037564"
---
# <a name="train-a-tensorflow-model-locally"></a>Eseguire il training di un modello TensorFlow in locale

Questa guida introduttiva descrive come eseguire il training di un modello TensorFlow con il set di dati [MNIST](http://yann.lecun.com/exdb/mnist/) in locale in Visual Studio Tools for AI.

Il database MNIST include un set di training di 60.000 esempi e un set di test di 10.000 esempi di cifre scritte a mano.

## <a name="prerequisites"></a>Prerequisiti

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

   ![Aprire il progetto](media/tensorflow-local/open-project.png)

   ![Aprire la soluzione](media/tensorflow-local/open-solution.png)

- Trovare il progetto MNIST in Esplora soluzioni , fare **clic** con il pulsante destro del mouse e scegliere **Imposta come Project**.

- Fare clic su **Start** (Avvia).

- L'output viene stampato nella console.

   ![Output di esempio dalla console](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Eseguire il training di un modello TensorFlow nel cloud](tensorflow-vm.md)
