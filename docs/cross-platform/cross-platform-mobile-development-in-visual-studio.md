---
title: Sviluppo di app per dispositivi mobili multipiattaforma in Visual Studio | Microsoft Docs
description: Questo articolo illustra come creare app per dispositivi Android, iOS e Windows usando Visual Studio.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: f2ce02467a43fc71a0e6e352a9a31a9ccfe810bf
ms.sourcegitcommit: d0061f62c8543ff0db500972d9402a7f00e017c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201767"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Sviluppo per dispositivi mobili multipiattaforma in Visual Studio

È possibile compilare app per i dispositivi Android, iOS e Windows usando Visual Studio.  Durante la progettazione dell'app, usare gli strumenti Visual Studio per aggiungere facilmente servizi connessi, ad esempio Microsoft 365, Servizio app di Azure e Application Insights.

Compilare le app usando C# e .NET Framework, HTML e JavaScript o C++. Condividere codice, stringhe, immagini e in alcuni casi anche l'interfaccia utente.

Per compilare un gioco o un'app grafica immersiva, installare Visual Studio Tools per Unity e sfruttare tutte le potenti funzionalità di produttività di Visual Studio con Unity, il noto motore multipiattaforma e grafico e ambiente di sviluppo di app per iOS, Android, Windows e altre piattaforme.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Compilare un'app per Android, iOS e Windows (.NET Framework)

![Dispositivi](../cross-platform/media/homedevices.png "HomeDevices")

Con Visual Studio Tools per Xamarin è possibile creare una soluzione unica per Android, iOS e Windows, condividendo il codice e anche l'interfaccia utente.

|**Scopri di più**|
|--------------------|
|[Installare Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Informazioni su Xamarin in Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Documentazione di Xamarin sullo sviluppo di app per dispositivi mobili](/xamarin/) |
|[DevOps con app Xamarin](/xamarin/tools/ci/devops/) |
|[Informazioni sulle app Windows universali in Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Informazioni sulle analogie tra Swift e C#](https://aka.ms/scposter) (download.microsoft.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Creare un'unica base di codice per Android, iOS e Windows

 È possibile compilare app native per Android, iOS e Windows usando C# o F# (Visual Basic non è attualmente supportato).  Per iniziare, installare Visual Studio, selezionare l'opzione Sviluppo di applicazioni per dispositivi mobili **con .NET** nel programma di installazione.

 Se è già stato Visual Studio, eseguire nuovamente il **Programma di installazione di Visual Studio** e selezionare la stessa opzione Sviluppo di applicazioni per dispositivi mobili con **.NET** per Xamarin (come sopra).

 Una volta terminata l'installazione, i modelli di progetti verranno visualizzati nella finestra di dialogo **Nuovo progetto**. Il modo più semplice per trovare i modelli Xamarin è eseguire una ricerca con la parola "Xamarin".

 Xamarin espone le funzionalità native di Android, iOS e Windows come classi e metodi .NET. In questo modo, le app hanno accesso completo alle API e ai controlli nativi e hanno la stessa capacità di risposta delle app scritte in linguaggi di piattaforma nativi.

 Dopo aver creato un progetto, sarà possibile sfruttare tutte le funzionalità di produttività di Visual Studio. Ad esempio, si potrà usare una finestra di progettazione per creare le pagine e IntelliSense per esplorare le API native delle piattaforme mobili. Quando si è pronti a eseguire l'app e verificarne l'aspetto, è possibile usare l'emulatore di Android SDK ed eseguire le app di Windows in modo nativo. È anche possibile usare direttamente i dispositivi Android e Windows con tethering. Per i progetti iOS, connettersi a un Mac in rete e avviare l'emulatore iOS da Visual Studio oppure connettersi a un dispositivo con tethering.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Progettare un insieme di pagine che eseguono il rendering in tutti i dispositivi usando Xamarin.Forms

 A seconda della complessità della progettazione delle app, è possibile provare a compilare l'app con i modelli *Xamarin.Forms* nel gruppo di modelli di progetto **App per dispositivi mobili** . Xamarin.Forms è un Toolkit dell'interfaccia utente che consente di creare un'unica interfaccia da condividere tra Android, iOS e Windows Phone.  Quando si compila una soluzione Xamarin.Forms, si otterrà un'app per Android, un'app per iOS e un'app per Windows. Per altri dettagli, vedere [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) e la [documentazione di Xamarin.Forms](/xamarin/xamarin-forms/).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Condividere il codice tra app Android, iOS e Windows

 Se non si usa Xamarin.Forms e si sceglie di progettare singolarmente per ogni piattaforma, è possibile condividere la maggior parte del codice non di interfaccia utente tra progetti di piattaforma (Android, iOS e Windows). Sono incluse le logiche di business, l'integrazione cloud, l'accesso ai database e qualsiasi altro codice che faccia riferimento a .NET Framework. L'unico codice che non è possibile condividere è quello che fa riferimento a una specifica piattaforma.

 ![Condividere il codice tra Windows, iOS e Android](../cross-platform/media/sharecode.png "ShareCode")

 È possibile condividere il codice usando un progetto condiviso, un progetto della Libreria di classi portabile o entrambi. Alcuni codici potrebbero essere più adatti a un progetto condiviso, mentre altri a un progetto della Libreria di classi portabile.

|**Scopri di più**|
|--------------------|
|[Opzioni di condivisione del codice](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Opzioni di condivisione del codice con .NET](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Dispositivi Windows 10 destinazione

 ![Windows Dispositivi](../cross-platform/media/windowsdevices.png "Dispositivi Windows")

 Se si vuole creare una singola app destinata all'intera gamma dei dispositivi Windows 10, creare un'app di Windows universale. L'app verrà progettata usando un progetto singolo e il rendering delle pagine verrà eseguito correttamente, indipendentemente dal dispositivo usato per visualizzarle.

 Iniziare con un modello di progetto per un'app della piattaforma UWP (Universal Windows Platform). Progettare visivamente le pagine e quindi aprirle in una finestra di anteprima per verificare come vengono visualizzate per vari tipi di dispositivi. Se l'aspetto di una pagina su un dispositivo non è di proprio gradimento, è possibile ottimizzare la pagina in modo da adattarla alle dimensioni dello schermo, alla risoluzione o ai vari orientamenti, ad esempio la modalità orizzontale o verticale. Tutto ciò è possibile grazie alle intuitive finestre degli strumenti e a opzioni di menu facilmente accessibili in Visual Studio. Quando si è pronti a eseguire l'app e il codice un'istruzione alla volta, sono disponibili tutti gli emulatori e i simulatori per diversi tipi di dispositivi, riuniti in un unico elenco a discesa nella barra degli strumenti **Standard**.

|**Scopri di più**|
|--------------------|
|[Introduzione alla piattaforma UWP (Universal Windows Platform)](/windows/uwp/get-started/universal-application-platform-guide)|
|[Creare la prima app](/windows/uwp/get-started/your-first-app)|
|[Sviluppare app per la piattaforma UWP (Universal Windows Platform)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Creare un'app per Android, iOS e Windows (HTML/JavaScript)

 ![Dispositivi Windows, iOS e Android](../cross-platform/media/homedevices.png "Dispositivi Windows, iOS e Android")

 Gli sviluppatori Web che hanno familiarità con HTML e JavaScript possono sviluppare per Windows, Android e iOS tramite gli Strumenti di Visual Studio per Apache Cordova. Queste app possono essere destinate a tutte e tre le piattaforme e possono essere compilate usando le competenze e i processi con cui si ha maggiore dimestichezza.

 Apache Cordova è un framework che include un modello di plug-in. Questo plug-in offre una singola API JavaScript che è possibile usare per accedere alle funzionalità native del dispositivo di tutte e tre le piattaforme (iOS, Android e Windows).

 Poiché queste API sono multipiattaforma, è possibile condividere la maggior parte del codice tra tutte e tre le piattaforme, con una conseguente riduzione dei costi di sviluppo e manutenzione. Non è necessario partire da zero: se sono stati creati altri tipi di applicazioni Web, è possibile condividere tali file con l'app Cordova senza doverli modificare o progettare nuovamente in alcun modo.

 ![App ibride per più dispositivi con JavaScript](../cross-platform/media/multidevicehybridapps.png "App ibride per più dispositivi con JavaScript")

 Per iniziare, installare Visual Studio e scegliere la funzionalità **Sviluppo di applicazioni per dispositivi mobili con JavaScript** durante l'installazione. Gli strumenti Cordova installano automaticamente tutti i software di terze parti necessari per compilare l'app multipiattaforma.

 Dopo aver installato l'estensione, aprire Visual Studio e creare un progetto **App vuota (Apache Cordova)**. È quindi possibile sviluppare l'app usando JavaScript o TypeScript. È anche possibile aggiungere i plug-in per estendere la funzionalità dell'app e visualizzare le API dei plug-in in IntelliSense durante la scrittura del codice.

 Quando si è pronti ad eseguire l'app e ad eseguire il codice un'istruzione alla volta, scegliere un emulatore, ad esempio l'emulatore Apache Ripple o l'emulatore Android, un browser o un dispositivo che sia connesso direttamente al computer. Quindi, avviare l'app. Le app sviluppate in un computer Windows sono eseguibili anche sul computer stesso. Tutte queste opzioni sono integrate in Visual Studio come parte degli Strumenti di Visual Studio per Apache Cordova.

 I modelli di progetto per la creazione di app della piattaforma UWP (Universal Windows Platform) sono ancora disponibili in Visual Studio, quindi è possibile usarli se si intende destinare l'app solo ai dispositivi Windows. Se si vuole che l'app sia successivamente eseguibile anche in Android e iOS, è sempre possibile convertire il codice in un progetto Cordova.

|**Scopri di più**|
|--------------------|
|[Installare Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Introduzione a Strumenti di Visual Studio per Apache Cordova](/previous-versions/visualstudio/cross-platform/tools-for-cordova/)|
|[Informazioni sull'emulatore di Visual Studio per Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Creare un'app per Android, iOS e Windows (C++)

![Usare C&#43;&#43; per compilare per Android, iOS e Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Installare prima di tutto Visual Studio e il carico **di lavoro Sviluppo di applicazioni per dispositivi mobili con C++.** È quindi possibile compilare un'applicazione di attività nativa per Android o un'app destinata a Windows o iOS. Se si vuole, è possibile usare Android, iOS e Windows nella stessa soluzione e quindi condividere il codice tra di essi usando una libreria condivisa statica o dinamica multipiattaforma.

 Se si vuole compilare un'app per Android che richiede manipolazioni grafiche avanzate, ad esempio un videogioco, è possibile usare C++ a tale scopo. Iniziare con il **progetto Native Activity Application (Android).** Questo progetto contiene il supporto completo per la toolchain Clang.

 ![Modello di progetto di attività nativa](../cross-platform/media/cross-plat_cpp_native.png "Modello di progetto di attività nativa")

 Quando si è pronti per eseguire l'app e verificarne l'aspetto, usare l'emulatore Android. È veloce, affidabile e facile da installare e configurare.

 È anche possibile creare un'app destinata all'intera gamma di dispositivi Windows 10 usando C++ e un modello di progetto per un'app della piattaforma UWP (Universal Windows Platform). Per altre informazioni, vedere la sezione precedente [Sviluppare per dispositivi Windows 10](#WindowsHTML) in questo argomento.

 È possibile condividere il codice C++ tra Android, iOS e Windows creando una libreria condivisa statica o dinamica.

 ![Librerie statiche e dinamiche condivise](../cross-platform/media/cross_plat_cpp_libraries.png "Librerie statiche e dinamiche condivise")

 È possibile utilizzare tale libreria in un progetto Windows, iOS o Android, come quelli descritti in precedenza in questa sezione. È anche possibile usarla in un'app compilata con Xamarin, Java o qualsiasi linguaggio che consenta di richiamare le funzioni in una DLL non gestita.

 Quando si scrive il codice in queste librerie, è possibile usare IntelliSense per esplorare le API native delle piattaforme Android e Windows. Questi progetti di libreria sono completamente integrati con il debugger di Visual Studio in modo da poter impostare punti di interruzione, eseguire il codice seguendo un'istruzione alla volta nonché individuare e risolvere i problemi mediante tutte le funzionalità avanzate del debugger.

|**Scopri di più**|
|--------------------|
|[Download Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[Installare lo sviluppo di app per dispositivi mobili multipiattaforma con C++](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Altre informazioni sull'uso di C++ per più piattaforme](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Installare gli elementi necessari e quindi creare un'applicazione di attività nativa C++ per Android](/cpp/cross-platform/create-an-android-native-activity-app)|
|[Informazioni sulla condivisione del codice C++ con le app Android e Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Esempi di sviluppo di app per dispositivi mobili multipiattaforma per C++](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Creare un gioco multipiattaforma per Android, iOS e Windows usando Visual Studio Tools per Unity

 Visual Studio Tools per Unity è un'estensione gratuita di Visual Studio che integra gli strumenti efficienti di Visual Studio per la modifica del codice, la produttività e il debug con *Unity*, il motore grafico e per videogiochi multipiattaforma più diffuso nonché un ambiente di sviluppo di app immersive per Windows, iOS, Android e altre piattaforme, incluso il Web.

 ![Ambiente di sviluppo VSTU](../cross-platform/media/vstu_overview.png "Visual Studio Tools per Unity panoramica")

 Con Visual Studio Tools per Unity (VSTU) è possibile usare Visual Studio per scrivere script di giochi ed editor in C# e quindi usarne il potente debugger per individuare e correggere gli errori. La versione più recente di VSTU include il supporto di Unity 2018.1 e la colorazione della sintassi per il linguaggio ShaderLab di Unity, una migliore sincronizzazione con Unity, funzionalità di debug più complete e un miglioramento nella generazione del codice per la procedura guidata MonoBehavior. VSTU integra anche i file di progetto Unity, i messaggi della console e la possibilità di iniziare il gioco in Visual Studio evitando in tal modo di dover passare dall'editor di Unity a Visual Studio e viceversa durante la scrittura del codice.

|**Scopri di più**|
|--------------------|
|[Altre informazioni sulla compilazione di giochi Unity con Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Altre informazioni su Visual Studio Tools per Unity](/visualstudio/gamedev/unity/get-started/visual-studio-tools-for-unity) |
|[Iniziare a usare Visual Studio Tools per Unity](/visualstudio/gamedev/unity/get-started/getting-started-with-visual-studio-tools-for-unity) |
|[Informazioni sugli ultimi miglioramenti apportati a Visual Studio Tools per Unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog di Visual Studio)|
|[Guardare un video di introduzione a Visual Studio Tools per Unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408&preserve-view=true) (Video)|
|[Informazioni su Unity](https://unity.com/) (sito Web Unity)|

## <a name="see-also"></a>Vedi anche

- [Aggiungere Microsoft 365 API a un progetto Visual Studio](/office/developer-program/office-365-developer-program)
- [Servizi app di Azure: app per dispositivi mobili](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
