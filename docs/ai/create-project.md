---
title: Creare un progetto in Strumenti di Visual Studio per AI
description: Creare un progetto usando un campione dalla raccolta di Azure Machine Learning
keywords: ai, visual studio, azure machine learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how to article
ms.technology: visual studio
ms.devlang: multiple
ms.service: multiple
ms.openlocfilehash: 2d8b5f1d06d31eaba9c75e0f0515b2526fc7efdf
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Creare un progetto AI dalla raccolta di Azure Machine Learning in Visual Studio

Azure Machine Learning è integrato con Strumenti di Visual Studio per AI. È possibile usarlo per inviare processi di machine learning a destinazioni di calcolo remote come macchine virtuali di Azure, cluster Spark e così via. Vedere altre informazioni su [Sperimentazione di Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration) 

Dopo aver [installato Strumenti di Visual Studio per AI](installation.md) è facile creare un nuovo progetto Python usando i file recipe predefiniti nella raccolta di esempio Azure Machine Learning.

> ! Deve essere installato Azure Machine Learning Workbench. Per installarlo, vedere la [guida introduttiva all'installazione di Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation) 

1. Avviare Visual Studio. Aprire **Esplora Server** scegliendo il menu **AI Tools** (Strumenti AI) e quindi **Select Cluster** (Seleziona cluster).  

    ![Selezione di cluster](media\create-project\select-cluster.png)

1. Accedere alla sottoscrizione di Azure Machine Learning facendo clic con il pulsante destro del mouse sul nodo **Azure Machine Learning** in Esplora server, quindi selezionare **Accesso** e seguire le istruzioni.

    ![Accesso](media\create-project\azureml-login.png)
 
2. Selezionare **AI Tools (Strumenti AI) > Azure Machine Learning Sample Gallery (Raccolta di campioni di Azure Machine Learning)**. 
    
    ![Raccolta di campioni](media\create-project\gallery.png)

1. Per questa guida rapida, selezionare il campione "**MNIST using TensorFlow**" e fare clic su **Installa**. Specificare 
2.
 - **Gruppo di risorse**: gruppo di risorse di Azure in cui verranno archiviati i metadati
 - **Account**: account di prova di Azure Machine Learning
 - **Area di lavoro**: area di lavoro di Azure Machine Learning
 - **Tipo di progetto**: framework di machine learning. In questo caso scegliere **TensorFlow**
 - **Aggiungi a soluzione**: determina se aggiungere il progetto alla soluzione di Visual Studio corrente o se creare e aprire una nuova soluzione
 - **Percorso progetto**: percorso in cui salvare il codice
 - **Nome progetto**: digitare **TensorFlowMNIST**
   

    ![Progetto risultante quando si usa il modello di applicazione Python](media\create-project\new-AzureSampleProject.png)

1. Visual Studio crea il file di progetto (un file `.pyproj` su disco) e gli altri file definiti nel campione. Con il modello "MNIST" il progetto contiene più file.

    ![mnist](media\create-project\azml-mnist.png)

1. Inviare il processo ad Azure Machine Learning. 

    ![mnist](media\create-project\submit-azml.png)

1. Eseguire in un contenitore Docker o nel computer locale

    ![mnist](media\create-project\azml-local.png)