---
title: Eseguire un modello TensorFlow nel cloud
description: eseguire un modello tensorflow in una macchina virtuale per l'apprendimento avanzato di azure
keywords: intelligenza artificiale, visual studio, macchina virtuale per l'apprendimento avanzato
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 0a73a22397f05660cd0b5e2c90633f6528297848
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633307"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Eseguire il training di un modello TensorFlow nel cloud

Questa esercitazione illustra le procedure per il training di un modello TensorFlow usando il [set di dati MNIST](http://yann.lecun.com/exdb/mnist/) in una macchina virtuale per l'[apprendimento avanzato](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) (DLVM, Deep Learning Virtual Machine) di Azure.

Il database MNIST include un set di training di 60.000 esempi e un set di test di 10.000 esempi di cifre scritte a mano.

## <a name="prerequisites"></a>Prerequisiti
Prima di iniziare, assicurarsi di aver installato e configurato quanto segue:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Configurare la macchina virtuale di Azure per l'apprendimento avanzato

> [!NOTE]
> Impostare **Tipo di sistema operativo** su Linux.

È possibile trovare [qui](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm) istruzioni per la configurazione di una macchina virtuale per l'apprendimento avanzato.

### <a name="remove-comment-in-parens"></a>Rimuovere il commento tra parentesi

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Scaricare il codice di esempio

Scaricare questo [repository di GitHub](https://github.com/Microsoft/samples-for-ai) contenente esempi per iniziare ad approfondire TensorFlow, CNTK, Theano e altro ancora.

## <a name="open-project"></a>Aprire il progetto

- Avviare Visual Studio e selezionare **File > Apri > Progetto/Soluzione**.

- Selezionare la cartella **TensorflowExamples** dal repository degli esempi scaricato e aprire il file **TensorflowExamples.sln**.

   ![Aprire il progetto](media/tensorflow-local/open-project.png)

   ![Aprire la soluzione](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Aggiungere una macchina virtuale remota di Azure

In Esplora server fare clic con il pulsante destro del mouse sul nodo **Remote Machines** (Macchine remote) nel nodo AI Tools (Strumenti AI) e scegliere "Aggiungi" (Aggiungi). Immettere nome visualizzato, host IP, porta SSH, nome utente e password/file di chiave della macchina virtuale remota.

![Aggiungere una nuova macchina virtuale remota](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Inviare il processo alla macchina virtuale di Azure
In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto MNIST e scegliere **Invia processo**.

![Invio di un processo a una macchina virtuale remota](media/tensorflow-vm/job-submission.png)

Nella finestra di invio:

- Nell'elenco **Usa cluster** selezionare la macchina virtuale remota (con prefisso "rm:") a cui inviare il processo.

- Immettere un Nome **processo**.

- Fare clic su **Submit** (Invia).

## <a name="check-status-of-job"></a>Controllare lo stato del processo
Per visualizzare lo stato e i dettagli dei processi, espandere la macchina virtuale a cui è stato inviato il processo in **Esplora server**. Fare doppio clic su **Processi**.

![Browser processi](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Pulire le risorse

Arrestare la macchina virtuale se non si prevede di usarla entro breve. Dopo aver completato le operazioni con l'esercitazione, eseguire il comando seguente per pulire le risorse:

```azurecli-interactive
az group delete --name myResourceGroup
```
