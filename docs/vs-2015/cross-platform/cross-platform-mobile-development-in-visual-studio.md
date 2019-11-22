---
title: Sviluppo di app per dispositivi mobili multipiattaforma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 27f6ee12d7404c77e4994a4e89cf23c9b3cdef0f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297898"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Sviluppo di app per dispositivi mobili multipiattaforma in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile compilare app per i dispositivi Android, iOS e Windows usando Visual Studio.  Durante la progettazione delle app, usare gli strumenti in Visual Studio per aggiungere facilmente i servizi connessi, ad esempio Office 365, Servizi app di Azure e Application Insights.

 Compilare le app usando C# e .NET Framework, HTML e JavaScript o C++. Condividere codice, stringhe, immagini e in alcuni casi anche l'interfaccia utente.

 Per compilare un gioco o un'app grafica immersiva, installare Visual Studio Tools per Unity e sfruttare tutte le potenti funzionalità di produttività di Visual Studio con Unity, il noto motore multipiattaforma e grafico e ambiente di sviluppo di app per iOS, Android, Windows e altre piattaforme.

 **Contenuto dell'articolo:**

- [Compilare un'app per Android, iOS e Windows (.NET Framework)](#NET)

  - [Creare un'unica base di codice per Android, iOS e Windows](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Sviluppare per dispositivi Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Compilare un'app per Android, iOS e Windows (HTML/JavaScript)](#HTML)

- [Compilare un'app per Android e Windows (C++)](#CPP)

- [Creare un gioco multipiattaforma per Android, iOS e Windows usando Visual Studio Tools per Unity](#Unity)

## <a name="NET"></a> Compilare un'app per Android, iOS e Windows (.NET Framework)
 ![Dispositivi](../cross-platform/media/homedevices.png "HomeDevices")

 Con Xamarin è possibile creare una soluzione unica per Android, iOS e Windows, condividendo il codice e anche l'interfaccia utente.

|**Altre informazioni**|
|--------------------|
|[Installare Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Informazioni su Xamarin in Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio e Xamarin](../cross-platform/visual-studio-and-xamarin.md) (MSDN Library)|
|[Application Lifecycle Management (ALM) con app Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (MSDN Library)|
|[Informazioni sulle app per Windows universale in Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Informazioni sulle analogie tra Swift e C#](https://aka.ms/scposter) (download.microsoft.com)|
|[Informazioni sull'emulatore di Visual Studio per Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="AndroidHTML"></a> Creare un'unica base di codice per Android, iOS e Windows
 È possibile compilare app native per Windows, iOS e Android tramite C# o F# (Visual Basic non è attualmente supportato).  Per iniziare, installare Visual Studio 2015, selezionare l'opzione **Personalizzato** nel programma di installazione e selezionare la casella sotto **Sviluppo di app per dispositivi mobili multipiattaforma > C#/ .NET (Xamarin)** . È possibile iniziare anche con il [programma di installazione di Xamarin](https://www.xamarin.com/download), necessario per installare Xamarin per Visual Studio 2013.

 Se è già stato installato Visual Studio 2015, eseguire il programma di installazione da **Pannello di controllo > Programmi e funzionalità** e selezionare la stessa opzione **Personalizzato** per Xamarin, come illustrato in precedenza.

 Dopo aver eseguito l'installazione, i modelli di progetto vengono visualizzati nella finestra di dialogo **Nuovo progetto**. Il modo più semplice per trovare i modelli Xamarin è eseguire una ricerca con la parola "Xamarin".

 Xamarin espone le funzionalità native di Windows, iOS e Android come oggetti .NET. In questo modo le app hanno accesso completo alle API native e ai controlli utente nativi e hanno la stessa capacità di risposta delle app scritte in linguaggi di piattaforma nativa.

 Dopo aver creato un progetto, sarà possibile usare tutte le funzionalità di produttività di Visual Studio. Ad esempio, si potrà usare una finestra di progettazione per creare le pagine e IntelliSense per esplorare l'API nativa della piattaforma mobile. Quando si è pronti a eseguire l'app e verificarne l'aspetto, è possibile usare l'emulatore di Visual Studio per Android o l'emulatore SDK per Android SDK, eseguire le app Windows in modo nativo oppure eseguire le app Windows nell'emulatore di Windows Phone. È anche possibile usare direttamente i dispositivi Android e Windows con tethering. Per i progetti iOS, connettersi a un Mac in rete e avviare l'emulatore Mac da Visual Studio oppure connettersi a un dispositivo con tethering.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Progettare un insieme di pagine che eseguono il rendering in tutti i dispositivi usando Xamarin.Forms
 A seconda della complessità della progettazione delle app, è possibile provare a compilare l'app con i modelli *Xamarin.Forms* nel gruppo di modelli di progetto **App per dispositivi mobili** . Xamarin.Forms è un Toolkit dell'interfaccia utente che consente di creare un'unica interfaccia da condividere tra Android, iOS e Windows Phone.  Quando si compila una soluzione Xamarin.Forms, si otterrà un'app per Android, un'app per iOS e un'app per Windows. Per altri dettagli, vedere [Altre informazioni sullo sviluppo per dispositivi mobili con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="ShareHTML"></a> Condividere il codice tra app Android, iOS e Windows
 Se non si usa Xamarin.Forms e si sceglie di progettare singolarmente per ogni piattaforma, è possibile condividere la maggior parte del codice non di interfaccia utente tra progetti di piattaforma (Android, iOS e Windows). Sono incluse le logiche di business, l'integrazione cloud, l'accesso ai database e qualsiasi altro codice che faccia riferimento a .NET Framework. L'unico codice che non è possibile condividere è quello che fa riferimento a una specifica piattaforma.

 ![Condividi il codice tra l'interfaccia utente di Windows, iOs e Android](../cross-platform/media/sharecode.png "ShareCode")

 È possibile condividere il codice usando un progetto condiviso, un progetto della Libreria di classi portabile o entrambi. Alcuni codici potrebbero essere più adatti a un progetto condiviso, mentre altri a un progetto della Libreria di classi portabile.

|**Altre informazioni**|
|--------------------|
|Scegliere se condividere il codice usando i progetti condivisi, i progetti della Libreria di classi portabile o entrambi.<br /><br /> [Condivisione del codice tra piattaforme diverse](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (blog di .NET Framework)<br /><br /> [Opzioni di condivisione del codice](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Opzioni di condivisione del codice con .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (MSDN Library)|

### <a name="WindowsHTML"></a>Sviluppare per dispositivi Windows 10
 ![Dispositivi Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Se si vuole creare una singola app destinata all'intera gamma dei dispositivi Windows 10, creare un'app di Windows universale. L'app verrà progettata usando un singolo progetto e il rendering delle pagine verrà eseguito correttamente, indipendentemente dal dispositivo usato per visualizzarle.

 Iniziare con un modello di progetto app di Windows universale. Progettare visivamente le pagine e quindi aprirle in una finestra di anteprima per verificare come vengono visualizzate per vari tipi di dispositivi. Se l'aspetto di una pagina su un dispositivo non è di proprio gradimento, è possibile ottimizzare la pagina in modo da adattarla alle dimensioni dello schermo, alla risoluzione o ai vari orientamenti, ad esempio la modalità orizzontale o verticale. Tutto ciò è possibile grazie alle intuitive finestre degli strumenti e a opzioni di menu facilmente accessibili in Visual Studio. Quando si è pronti ad eseguire l'app e ad eseguire il codice un'istruzione alla volta, sono disponibili tutti gli emulatori e i simulatori per diversi tipi di dispositivi, riuniti in un unico elenco a discesa nella barra degli strumenti **Standard** .

 Windows 10 è relativamente nuovo, quindi sono disponibili anche modelli di progetto destinati a Windows 8.1. Con questii modelli di progetto le app saranno eseguibili anche su telefoni, tablet e PC Windows 10. Tuttavia, tutti i dispositivi che eseguono Windows 8.1 riceveranno un aggiornamento automatico a Windows 10; pertanto, a meno che vi siano motivi specifici per cui preferire Windows 8.1, è consigliabile usare i modelli di progetto destinati a Windows 10.

|**Altre informazioni**|
|--------------------|
|[Informazioni sulle app di Windows universale](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Dev Center)|
|[Compilare la prima app](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Dev Center)|
|[Sviluppare app per la piattaforma UWP (Universal Windows Platform)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrare le app alla piattaforma UWP (Universal Windows Platform)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="HTML"></a>Compilare un'app per Android, iOS e Windows (HTML/JavaScript)
 ![Dispositivi](../cross-platform/media/homedevices.png "HomeDevices")

 Gli sviluppatori Web che hanno conoscenza di HTML e JavaScript possono sviluppare per Windows, Android e iOS tramite gli Strumenti di Visual Studio per Apache Cordova. Queste app possono essere destinate a tutte e tre le piattaforme e possono essere compilate usando le competenze e i processi con cui si ha maggiore dimestichezza.

 Apache Cordova è un framework che include un modello di plug-in. Questo plug-in offre una singola API JavaScript che è possibile usare per accedere alle funzionalità native del dispositivo di tutte e tre le piattaforme (iOS, Android e Windows).

 Poiché queste API sono multipiattaforma, è possibile condividere la maggior parte del codice tra tutte e tre le piattaforme, con una conseguente riduzione dei costi di sviluppo e manutenzione. Inoltre, non è necessario partire da zero. Se sono stati creati altri tipi di applicazioni Web, è possibile condividere tali file con l'app Cordova senza doverli modificare o progettare nuovamente in alcun modo.

 ![App&#45;ibride per più dispositivi](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Per iniziare, installare Visual Studio 2015 e scegliere la funzionalità **HTML/JavaScript (Apache Cordova)** durante l'installazione. Se si usa Visual Studio 2013, installare l'estensione Strumenti di Visual Studio per Apache Cordova. In entrambi i casi, gli strumenti Cordova installano automaticamente tutti i software di terze parti necessari per compilare l'app multipiattaforma.

 Dopo aver installato l'estensione, aprire Visual Studio e creare un progetto **Applicazione vuota (Apache Cordova)** . È quindi possibile sviluppare l'app usando JavaScript o TypeScript. È anche possibile aggiungere i plug-in per estendere la funzionalità dell'app e visualizzare le API dei plug-in in IntelliSense durante la scrittura del codice.

 Quando si è pronti a eseguire l'app e il codice un'istruzione alla volta, scegliere un emulatore, ad esempio l'emulatore Apache Ripple o l'emulatore di Visual Studio per Android o Windows Phone, un browser o un dispositivo che sia connesso direttamente al computer. Quindi, avviare l'app. Le app sviluppate in un computer Windows, sono eseguibili anche sul computer stesso. Tutte queste opzioni sono integrate in Visual Studio come parte degli Strumenti di Visual Studio per Apache Cordova.

 I modelli di progetto per la creazione di app di Windows universale sono ancora disponibili in Visual Studio, quindi è possibile usarli se si prevede di interagire solo con dispositivi Windows. Se si vuole che l'app sia successivamente eseguibile anche in Android e iOS, è sempre possibile convertire il codice in un progetto Cordova. Esistono versioni open source delle API WinJS quindi è possibile riusare qualsiasi codice che usa tali API. Ciò premesso, se si prevede di interagire con altre piattaforme in futuro, è consigliabile iniziare con Strumenti di Visual Studio per Apache Cordova.

|**Altre informazioni**|
|--------------------|
|[Installare Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Introduzione a Visual Studio Tools per Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (taco.visualstudio.com)|
|[Informazioni sull'emulatore di Visual Studio per Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="CPP"></a>Compilare un'app per Android e Windows (C++)
 ![Usare C&#43; &#43; per compilare per Android, iOS e Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Installare prima Visual Studio 2015 e gli strumenti di sviluppo di app per dispositivi mobili multipiattaforma di Visual C++. Quindi, è possibile compilare un'applicazione NativeActivity per Android o un'app per Windows. I modelli C++ per iOS non sono ancora disponibili. Se si vuole, è possibile includere Android e Windows nella stessa soluzione e quindi condividere il codice tra le piattaforme usando una libreria condivisa statica o dinamica multipiattaforma.

 Se si vuole compilare un'app per Android che richiede manipolazioni grafiche avanzate, ad esempio un videogioco, è possibile usare C++ a tale scopo. Iniziare con il progetto **Applicazione NativeActivity (Android)** . Questo progetto contiene il supporto completo per la toolchain Clang.

 ![Modello di progetto di attività Native](../cross-platform/media/cross-plat-cpp-native.png "Cross-Plat_CPP_Native")

 Quando si è pronti per eseguire l'app e verificarne l'aspetto, è possibile usare l'emulatore di Visual Studio per Android. È veloce, affidabile e facile da installare e configurare.

 È anche possibile creare una singola app destinata all'intera gamma dei dispositivi Windows 10 usando C++ e un modello di progetto app di Windows universale. Per altre informazioni, vedere la sezione precedente [Sviluppare per dispositivi Windows 10](#WindowsHTML) in questo argomento.

 È possibile condividere il codice C++ tra Android e Windows creando una libreria condivisa statica o dinamica.

 ![Librerie condivise statiche e dinamiche](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 È possibile usare tale libreria in un progetto Windows o Android, come quelli descritti in precedenza in questa sezione. È anche possibile usarla in un'app compilata con Xamarin, Java o qualsiasi linguaggio che consenta di richiamare le funzioni in una DLL non gestita.

 Quando si scrive il codice in queste librerie, è possibile usare IntelliSense per esplorare le API native delle piattaforme Android e Windows. Questi progetti di libreria sono completamente integrati con il debugger di Visual Studio in modo da poter impostare punti di interruzione, eseguire il codice seguendo un'istruzione alla volta nonché individuare e risolvere i problemi mediante tutte le funzionalità avanzate del debugger.

|**Altre informazioni**|
|--------------------|
|[Scaricare Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Installare gli strumenti Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|
|[Altre informazioni sull'uso di C++ per interagire con più piattaforme.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Installare gli strumenti necessari, quindi creare un'applicazione NativeActivity per Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|
|[Informazioni sull'emulatore di Visual Studio per Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Informazioni sulla condivisione del codice C++ con le app Android e Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Esempi di Sviluppo di app per dispositivi mobili multipiattaforma per C++](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Library)|
|[Altri esempi di Sviluppo di app per dispositivi mobili multipiattaforma per C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

## <a name="Unity"></a> Creare un gioco multipiattaforma per Android, iOS e Windows usando Visual Studio Tools per Unity
 Visual Studio Tools per Unity è un'estensione gratuita di Visual Studio che integra gli strumenti efficienti di Visual Studio per la modifica del codice, la produttività e il debug con *Unity*, il motore grafico e per videogiochi multipiattaforma più diffuso nonché un ambiente di sviluppo di app immersive per Windows, iOS, Android e altre piattaforme, incluso il Web.

 ![Ambiente di sviluppo VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Con Visual Studio Tools per Unity (VSTU) è possibile usare Visual Studio per scrivere script di giochi ed editor in C# e quindi usarne il potente debugger per individuare e correggere gli errori. La versione più recente di VSTU include il supporto di Unity 5 e la colorazione della sintassi per il linguaggio ShaderLab di Unity, una migliore sincronizzazione con Unity, funzionalità di debug più complete e un miglioramento nella generazione del codice per la procedura guidata MonoBehavior. VSTU integra anche i file di progetto Unity, i messaggi della console e la possibilità di iniziare il gioco in Visual Studio evitando in tal modo di dover passare dall'editor di Unity a Visual Studio e viceversa durante la scrittura del codice.

 Iniziare subito a creare un gioco con Unity e Visual Studio Tools per Unity.

|**Altre informazioni**|
|--------------------|
|[Altre informazioni sulla compilazione di giochi Unity con Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Altre informazioni su Visual Studio Tools per Unity](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Library)|
|[Iniziare a usare Visual Studio Tools per Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Library)|
|[Informazioni sugli ultimi miglioramenti apportati a Visual Studio Tools per Unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog di Visual Studio)|
|[Guardare un video di introduzione a Visual Studio Tools per Unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Informazioni su Unity](https://unity.com/) (sito Web Unity)|

## <a name="see-also"></a>Vedere anche

- [Aggiungere le API di Office 365 a un progetto di Visual Studio](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Servizi mobili di Azure](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
