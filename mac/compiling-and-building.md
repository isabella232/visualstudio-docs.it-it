---
title: Compilazione e creazione in Visual Studio per Mac | Microsoft Docs
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: abf772f1e00239b3a66e01c95dd827a392a12902
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilazione e creazione di build in Visual Studio per Mac

Visual Studio per Mac consente di compilare applicazioni e creare assembly durante lo sviluppo del progetto. È importante compilare il codice e creare build già nelle prime fasi e spesso, per consentire l'identificazione di tipi non corrispondenti e di altri errori in fase di compilazione.

## <a name="building-from-the-ide"></a>Compilazione nell'IDE

Visual Studio per Mac consente di creare ed eseguire build immediatamente, mantenendo al contempo il controllo della funzionalità di creazione della build. Il sistema di creazione di build di Visual Studio per Mac è MSBuild.

Tutti i progetti e tutte le soluzioni create nell'interfaccia IDE hanno una configurazione di compilazione predefinita, che definisce il contesto per le build. Queste configurazioni possono essere modificate. In alternativa, è possibile creare configurazioni personalizzate. La creazione e la modifica di queste configurazioni aggiorna automaticamente il file di progetto, che viene quindi usato da MSBuild per la compilazione.  

Per altre informazioni su come compilare progetti e soluzioni nell'IDE, vedere la guida [Compilazione e pulizia di progetti e soluzioni](~/building-and-cleaning-projects-and-solutions.md).

Visual Studio per Mac consente anche di eseguire le operazioni seguenti:

* Modificare il percorso di output. È possibile eseguire questa operazione nelle opzioni del progetto:

    ![Modificare il percorso di output](media/compiling-and-building-image4.png)

* Modificare il livello di dettaglio dell'output di compilazione:

    ![Modificare il livello di dettaglio della compilazione](media/compiling-and-building-image5.png)

* Aggiungere comandi personalizzati prima, durante o dopo la compilazione o la pulizia:

    ![Aggiungere comandi personalizzati](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Compilazione dalla riga di comando

È possibile usare il motore di compilazione MSBuild per compilare applicazioni tramite la riga di comando.

Per altre informazioni sull'uso di MSBuild, vedere il contenuto in [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

## <a name="building-from-visual-studio-team-services"></a>Compilazione da Visual Studio Team Services

* [Build your Xamarin App](https://www.visualstudio.com/docs/build/apps/mobile/xamarin) (Compilare l'app Xamarin)
* [Continuous Integration with Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/) (Integrazione continua con Xamarin)