---
title: Compilazione e creazione di build
description: Questo articolo descrive come creare e compilare progetti e soluzioni in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: 2fed47263740ed1f60997540eb65ce25217bc3a03984890d408a3dfac68de3f5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121439969"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilazione e creazione di build in Visual Studio per Mac

Visual Studio per Mac consente di compilare applicazioni e creare assembly durante lo sviluppo del progetto. È importante compilare il codice e creare build già nelle prime fasi e spesso, per consentire l'identificazione di tipi non corrispondenti e di altri errori in fase di compilazione.

## <a name="building-from-the-ide"></a>Compilazione nell'IDE

Visual Studio per Mac consente di creare ed eseguire build immediatamente, mantenendo al contempo il controllo della funzionalità di creazione della build. Il sistema di creazione di build di Visual Studio per Mac è MSBuild.

Tutti i progetti e tutte le soluzioni create nell'interfaccia IDE hanno una configurazione di compilazione predefinita, che definisce il contesto per le build. Queste configurazioni possono essere modificate. In alternativa, è possibile creare configurazioni personalizzate. La creazione e la modifica di queste configurazioni aggiorna automaticamente il file di progetto, che viene quindi usato da MSBuild per la compilazione.

Per altre informazioni su come compilare progetti e soluzioni nell'IDE, vedere la guida [Compilazione e pulizia di progetti e soluzioni](building-and-cleaning-projects-and-solutions.md).

Visual Studio per Mac consente anche di eseguire le operazioni seguenti:

* Modificare il percorso di output. È possibile eseguire questa operazione nelle opzioni del progetto:

    ![Modificare il percorso di output](media/compiling-and-building-image4.png)

* Modificare il livello di dettaglio dell'output di compilazione:

    ![Modificare il livello di dettaglio della compilazione](media/compiling-and-building-image5.png)

* Aggiungere comandi personalizzati prima, durante o dopo la compilazione o la pulizia:

    ![Aggiungere comandi personalizzati](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Compilazione dalla riga di comando

È possibile usare il motore di compilazione MSBuild per compilare applicazioni tramite la riga di comando.

Per altre informazioni sull'uso di MSBuild, vedere il contenuto in [MSBuild](/visualstudio/msbuild/msbuild).

## <a name="building-from-azure-pipelines"></a>Compilazione da Azure Pipelines

* [Creare l'app Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&preserve-view=true&tabs=vsts)
* [Continuous Integration with Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/) (Integrazione continua con Xamarin)

## <a name="see-also"></a>Vedi anche

- [Compilazione e creazione (Visual Studio in Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)