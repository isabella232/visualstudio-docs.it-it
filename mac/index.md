---
title: Introduzione a Visual Studio per Mac
description: In questo articolo vengono illustrate le funzionalità di Visual Studio per Mac
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 59e349b1d784e68c3ef6842834d875ce5d1917bb
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315553"
---
# <a name="visual-studio-for-mac"></a>Visual Studio per Mac

Visual Studio per Mac è un IDE moderno e avanzato dotato di molte funzionalità per la creazione di applicazioni mobili, desktop e Web. Supporta i tipi di sviluppo seguenti:

- App per dispositivi mobili con .NET: Android, iOS, tvOS, watchOS
- App desktop Mac
- Applicazioni .NET Core
- Applicazioni Web ASP.NET Core
- Giochi Unity multipiattaforma

Include funzionalità quali un editor avanzato, funzioni di debug, integrazione di piattaforme native con iOS, Mac e Android e controllo integrato del codice sorgente.

Questo articolo descrive diverse sezioni di Visual Studio per Mac e presenta alcune delle caratteristiche che lo rendono uno strumento potente per la creazione di applicazioni multipiattaforma.

> [!TIP]
> L'**anteprima di Visual Studio 2019 per Mac** è ora disponibile per i test. Seguire queste [istruzioni di installazione](/visualstudio/mac/installation/?view=vsmac-2019) e vedere la [presentazione dell'IDE 2019](/visualstudio/mac/ide-tour/?view=vsmac-2019).

## <a name="installation"></a>Installazione

Seguire i passaggi nella guida di [Installazione](install-preview.md) per scaricare e installare Visual Studio per Mac.

## <a name="language-support"></a>Supporto delle lingue

Visual Studio per Mac supporta lo sviluppo in C# e F# per impostazione predefinita.

### <a name="c"></a>C#

C# è il linguaggio di programmazione più usato per la creazione di applicazioni multipiattaforma in Visual Studio per Mac. L'IDE include il supporto completo per tutte le funzionalità di C# 7.

### <a name="f"></a>F#

F# è un linguaggio di programmazione funzionale e fortemente tipizzato, progettato per essere eseguito in .NET. È disponibile come linguaggio di programmazione per gli utenti di Visual Studio per Mac in Android, Mac e iOS. Per altre informazioni sull'uso di F# e per visualizzare esempi creati in questo linguaggio, consultare le guide su [F#](https://developer.xamarin.com/guides/cross-platform/fsharp/).

## <a name="platform-support"></a>Supporto per piattaforme

## <a name="net-core"></a>.NET Core

[.NET core](https://www.microsoft.com/net/core#macos) è una piattaforma per la creazione di applicazioni che vengono eseguite in Windows, Linux e Mac. Visual Studio per Mac include il supporto per il caricamento, la creazione, l'esecuzione e il debug dei progetti .NET Core. 

Per eseguire progetti .NET Core, è necessario scaricare e installare .NET Core SDK.

Supporto di .NET Core:

- IntelliSense C# e F#.
- Modelli di progetto .NET Core per console, libreria e applicazioni Web.
- Completo supporto per il debug, inclusi punti di interruzione, stack di chiamate, finestra Espressioni di controllo e così via.
- NuGet PackageReferences e ripristino basato su MSBuild.
- Supporto per il testing unità integrato per test di esecuzione e di debug con la piattaforma di test di Visual Studio inclusa in .NET Core SDK.
- Migrazione dal precedente formato project.json.

Per iniziare, esaminare il [laboratorio pratico](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started) sulle app Web ASP.NET Core.

## <a name="xamarin-mobile-app-development"></a>Sviluppo di app per dispositivi mobili Xamarin

Grazie a un eccellente supporto per [Xamarin](https://developer.xamarin.com/) è possibile sviluppare straordinarie app native per Android, macOS, iOS, tvOS e watchOS. Le applicazioni Xamarin.Forms multipiattaforma consentono di condividere il codice dell'interfaccia utente basato su XAML tra Android, iOS e macOS senza limitare l'accesso alle funzionalità native.

Per iniziare, esaminare il [laboratorio pratico](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started) sulle app per dispositivi mobili.

### <a name="android"></a>Android

Visual Studio dispone di un proprio Android SDK Manager integrato.

Per le applicazioni Android, Visual Studio per Mac include una propria finestra di progettazione, utilizzabile con file Android `.axml` per creare visivamente le interfacce utente. Visual Studio per Mac apre questi file nella propria finestra di progettazione Android, come illustrato nella figura seguente:

![Finestra di progettazione interfaccia utente Android](media/intro-image31.png)

Per altre informazioni sulla finestra di progettazione di Android, vedere il documento [Designer Overview](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview) (Panoramica della finestra di progettazione).

### <a name="ios"></a>iOS

La finestra di progettazione di iOS è pienamente integrata in Visual Studio per Mac e consente la modifica sul posto di file XIB e Storyboard per creare interfacce utente e transizioni iOS, tvOS e watchOS. L'intera interfaccia utente può essere compilata tramite la funzionalità di trascinamento della selezione tra la casella degli strumenti e l'area di progettazione, usando al contempo un approccio intuitivo alla gestione degli eventi. La finestra di progettazione di iOS supporta [controlli personalizzati](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/) con il vantaggio aggiunto del rendering in fase di progettazione.

![Finestar di progettazione storyboard iOS](media/intro-image30.png)

Per altre informazioni sull'uso della finestra di progettazione di iOS, vedere i documenti sulla [finestra di progettazione](https://developer.xamarin.com/guides/ios/user_interface/designer).

### <a name="mac"></a>Mac

Xamarin offre associazioni API Mac native che consentono di creare applicazioni Mac efficaci.

Per altre informazioni sulla scrittura di applicazioni Mac con Visual Studio per Mac, vedere la documentazione di [Xamarin.Mac](https://developer.xamarin.com/guides/#mac).

## <a name="gaming"></a>Giochi

Visual Studio per Mac offre supporto per lo sviluppo di giochi multipiattaforma con Unity 5.6.1.

Per iniziare, esaminare il [laboratorio pratico](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started) su Unity.

## <a name="enterprise-features"></a>Funzionalità aziendali

> [!Note]
> Questi prodotti sono utilizzabili solo con una sottoscrizione di Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Xamarin Profiler dispone di tre strumenti per la profilatura. La guida [Introduzione a Xamarin Profiler](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/) descrive le misure di questi strumenti e le relative modalità di analisi dell'applicazione, oltre a chiarire il significato dei dati presentati in ogni schermo.

### <a name="inspector"></a>Inspector

Xamarin Inspector offre una console C# interattiva con strumenti disponibili agli utenti. Può essere usato come supporto per il debug o per la diagnostica durante il controllo delle applicazioni attive, come strumento di formazione, di documentazione o sperimentazione.

![Xamarin Inspector](media/intro-inspector.png)

È costituito da un'applicazione autonoma che rappresenta una console C# che può avere come destinazioni varie piattaforme di programmazione (Android, iOS, Mac e Windows) e può integrarsi nel flusso di lavoro di debug dell'IDE. 

Per altre informazioni, vedere la guida di [Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/).

## <a name="next-steps"></a>Passaggi successivi

- **Panoramica**: per una panoramica di molte delle principali funzionalità in Visual Studio per Mac, vedere la relativa [panoramica sull'IDE](/visualstudio/mac/ide-tour/).
- **Installazione**: per informazioni su come scaricare e installare Visual Studio 2017 per Mac, vedere la guida di [installazione](/visualstudio/mac/installation/?view=vsmac-2017).
- **Esercitazioni di Xamarin**: per altre informazioni su come sviluppare codice con Xamarin, visitare il [Developer Center](https://developer.xamarin.com) (Centro sviluppatori) di Xamarin.
- **Video**: per altre informazioni su altre funzionalità e aspetti di Visual Studio per Mac, guardare i video sul sito Web di [Xamarin University](https://university.xamarin.com).
- **Laboratori pratici**: per iniziare a lavorare con i vari carichi di lavoro inclusi in Visual Studio per Mac, consultare i [laboratori pratici](https://github.com/Microsoft/vs4mac-labs).
