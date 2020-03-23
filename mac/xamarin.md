---
title: Xamarin
description: "L'uso di Xamarin in Visual Studio per Mac consente di creare applicazioni multipiattaforma per iOS, Mac, Android, tvOS e watchOS "
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.openlocfilehash: 31fb7fa4c2a87820285809d24b98fe8e59a6be01
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714473"
---
# <a name="xamarin-mobile-app-development"></a>Sviluppo di app per dispositivi mobili Xamarin

Grazie a un eccellente supporto per [Xamarin](/xamarin) è possibile sviluppare straordinarie app native per Android, macOS, iOS, tvOS e watchOS. Le applicazioni Xamarin.Forms multipiattaforma consentono di condividere il codice dell'interfaccia utente basato su XAML tra Android, iOS e macOS senza limitare l'accesso alle funzionalità native.

## <a name="xamarinforms"></a>Xamarin.Forms

XAML Hot Reload for Xamarin.Forms è integrato in Visual Studio per Mac nella versione 8.3 e successive. Con questa funzionalità abilitata le modifiche si riflettono immediatamente nella tua app in esecuzione ogni volta che salvi il file.

XAML Hot Reload può essere abilitato selezionando la casella di controllo **Abilita Xamarin Hot Reload** in **Preferenze > > Progetti > di Visual Studio > Xamarin Hot Reload**.

Per ulteriori informazioni su Hot Reload, vedere la [guida XAML Hot Reload for Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload) all'interno della documentazione.

## <a name="android"></a>Android

Visual Studio per Mac include uno strumento Android SDK Manager integrato che consente di accedere agli SDK di destinazione dell'app.

Per le applicazioni Android, Visual Studio per Mac include una propria finestra di progettazione, utilizzabile con file Android `.axml` per creare visivamente le interfacce utente. Visual Studio per Mac apre questi file nella propria finestra di progettazione Android, come illustrato nella figura seguente:

![Finestra di progettazione interfaccia utente Android](media/intro-image31.png)

Per altre informazioni su Android Designer, vedere la guida [Xamarin.Android Designer Overview](/xamarin/android/user-interface/android-designer/index) (Panoramica di Xamarin.Android Designer).

## <a name="ios"></a>iOS

La finestra di progettazione di iOS è pienamente integrata in Visual Studio per Mac e consente la modifica sul posto di file XIB e Storyboard per creare interfacce utente e transizioni iOS, tvOS e watchOS. L'intera interfaccia utente può essere compilata tramite la funzionalità di trascinamento della selezione tra la casella degli strumenti e l'area di progettazione, usando al contempo un approccio intuitivo alla gestione degli eventi. La finestra di progettazione di iOS supporta [controlli personalizzati](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) con il vantaggio aggiunto del rendering in fase di progettazione.

![Finestar di progettazione storyboard iOS](media/intro-image30.png)

Per altre informazioni sull'uso di iOS Designer, vedere le guide dello strumento [Designer](/xamarin/ios/user-interface/designer/?tabs=macos).

### <a name="mac"></a>Mac

Xamarin offre associazioni API Mac native che consentono di creare applicazioni Mac efficaci.

Per altre informazioni sulla scrittura di applicazioni Mac con Visual Studio per Mac, vedere le guide di [Xamarin.Mac](/xamarin/mac/get-started/index).

## <a name="xamarin-enterprise-features"></a>Funzionalità di Xamarin Enterprise

> [!Note]
> Questi prodotti sono utilizzabili solo con una sottoscrizione di Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Xamarin Profiler dispone di tre strumenti per la profilatura. La guida [Introduzione a Xamarin Profiler](/xamarin/tools/profiler/index?tabs=macos) descrive le misure di questi strumenti e le relative modalità di analisi dell'applicazione, oltre a chiarire il significato dei dati presentati in ogni schermo.

### <a name="inspector"></a>Inspector

Xamarin Inspector offre una console C# interattiva con strumenti disponibili agli utenti. Può essere usato come supporto per il debug o per la diagnostica durante il controllo delle applicazioni attive, come strumento di formazione, di documentazione o sperimentazione.

![Xamarin Inspector](media/intro-inspector.png)

È costituito da un'applicazione autonoma che rappresenta una console C# che può avere come destinazioni varie piattaforme di programmazione (Android, iOS, Mac e Windows) e può integrarsi nel flusso di lavoro di debug dell'IDE.

Per altre informazioni, vedere la guida di [Xamarin Inspector](/xamarin/tools/inspector/).
