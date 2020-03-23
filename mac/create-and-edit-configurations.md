---
title: Creazione e modifica di configurazioni della build
description: Questo articolo descrive la procedura di creazione delle configurazioni della build in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 26f6e25bfe1284fc31bcd484b905bf5d75c2ba15
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128430"
---
# <a name="creating-and-editing-build-configurations"></a>Creazione e modifica di configurazioni della build

Le configurazioni di compilazione offrono un controllo preciso su una build, consentendo di creare configurazioni per soddisfare diverse situazioni di test e distribuzione. È possibile creare configurazioni di compilazione per singoli progetti o a livello di soluzione.

È possibile creare nuove configurazioni e modificare quelle esistenti sia per i progetti che per le soluzioni utilizzando la finestra di dialogo Opzioni progetto.

>[!NOTE]
>Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [Procedura: Creare e modificare configurazioni](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Creazione di una configurazione di compilazione del progettoCreating a project build configuration

Per creare una configurazione di compilazione del progetto, attenersi alla seguente procedura:

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e selezionare **Opzioni**. È anche possibile fare doppio clic sul nodo del progetto per visualizzare la finestra di dialogo Opzioni progetto.

2. Nella finestra di dialogo Opzioni progetto selezionare **Compilazione > Configurazioni**:

    ![Gestione delle configurazioni in Opzioni progetto](media/create-and-edit-configurations-image2.png)

3. Selezionare **Aggiungi** per creare una nuova configurazione. È inoltre possibile copiare una qualsiasi delle configurazioni esistenti.

Dopo aver creato la configurazione, è possibile usare la sezione **Compilazione** in Opzioni progetto per adattare le proprietà appropriate alla configurazione:

![Configurare le opzioni di compilazione](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Creazione di una configurazione della build di una soluzione

Per creare una configurazione di compilazione della soluzione, attenersi alla seguente procedura:

1. Fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Opzioni**. È anche possibile fare doppio clic sul nodo della soluzione per visualizzare la finestra di dialogo Opzioni soluzione.

2. Nella finestra di dialogo Opzioni soluzione selezionare **Compilazione > Configurazioni**:

    ![Gestione delle configurazioni in Opzioni soluzione](media/create-and-edit-configurations-image1.png)

3. Selezionare **Aggiungi** per creare una nuova configurazione. È inoltre possibile copiare una qualsiasi delle configurazioni esistenti.

Dopo aver creato la configurazione, è possibile utilizzare la sezione **Compilazione** della finestra di dialogo Opzioni progetto per ognuno dei progetti per adattare le proprietà appropriate alla configurazione:

![Configurare le opzioni di compilazione](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Ridenominazione di una configurazione di compilazione

Per rinominare una configurazione, selezionarla dall'elenco Configurazione passando a **Compilazione > configurazioni** in Opzioni progetto o Soluzione:To rename a configuration, select it from the Configuration list by navigating to Build > Configurations in the Project or Solution Options:

![Elenco delle configurazioni](media/create-and-edit-configurations-image4.png)

Selezionare il pulsante **Rinomina**.

![Finestra di dialogo Rinomina](media/create-and-edit-configurations-image5.png)

Quindi fare clic **su OK** per confermare.

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare e modificare le configurazioni](/visualstudio/ide/how-to-create-and-edit-configurations)