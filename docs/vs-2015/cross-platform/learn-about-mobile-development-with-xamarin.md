---
title: Informazioni sullo sviluppo per dispositivi mobili con Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 4d75c93f2ff1678b1d9790462bc816ea35f8acd9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662075"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Altre informazioni sullo sviluppo per dispositivi mobili con Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene fatto riferimento a materiale introduttivo che fornisce informazioni sullo sviluppo di app per dispositivi mobili multipiattaforma con Xamarin. Se Visual Studio e Xamarin non sono ancora stati installati, avviare innanzitutto il processo [Setup and install](../cross-platform/setup-and-install.md) , quindi tornare qui per consultare queste risorse mentre i programmi di installazione sono in esecuzione.  
  
> [!NOTE]
>  Se non diversamente specificato, inizialmente è consigliabile leggere solo le pagine collegate direttamente a questo argomento e non le pagine secondarie. Se il processo di installazione è ancora in esecuzione dopo aver completato questo elenco, è possibile tornare indietro ed esplorare argomenti aggiuntivi.  
>   
>  È anche possibile leggere gli argomenti contrassegnati come "Concetti di base" e tornare agli argomenti "Approfondimento" più avanti.  
  
## <a name="essentials-introduction-to-xamarin"></a>Concetti di base: Introduzione a Xamarin  
 *10-20 minuti*  
  
1.  [App per dispositivi mobili in Visual Studio con Xamarin](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) fornisce un resoconto molto breve delle caratteristiche principali di Xamarin.  
  
2.  [Creazione di app per dispositivi mobili multipiattaforma con C# e Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel 9, 15 minuti e 16 secondi) con l'esperto di Xamarin James Montemagno. I primi tre minuti offrono una panoramica di Xamarin, seguita da dimostrazioni di codice.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Concetti di base: Panoramica dell'ambiente Visual Studio e Xamarin  
 *5-15 minuti*  
  
- Il computer Windows con Visual Studio e Xamarin è il sistema in cui verrà eseguita la maggior parte del lavoro. In questo computer verranno direttamente create le app Windows e Android, che saranno quindi eseguite e di cui sarà effettuato il debug in un dispositivo o un emulatore. È anche possibile compilare, eseguire ed effettuare il debug di app iOS in modalità remota tramite il Mac. Visual Studio nel computer Windows può anche connettersi alla finestra di progettazione dello storyboard e al simulatore iOS.  
  
- Il Mac con Xcode e Xamarin opera come host di compilazione/firma e ambiente di runtime per le app iOS. Le compilazioni per iOS da Visual Studio nel computer Windows sono delegate a questo Mac. Durante il debug di un'app iOS da Visual Studio, questa viene eseguita nel simulatore iOS nel Mac o direttamente in un dispositivo con tethering connesso al Mac. In questo caso si interagirà con l'app nel Mac o in prossimità di tale sistema e l'esperienza di debug avrà luogo in Visual Studio.  
  
  Queste relazioni sono illustrate di seguito. Altre informazioni sull'uso delle app iOS sono inoltre disponibili nell' [introduzione a Xamarin.iOS per Visual Studio](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/) (xamarin.com).  
  
  ![Relazione tra computer di sviluppo Windows e Mac in un ambiente Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin Learn 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Concetti di base: Struttura dei progetti  
 *10-30 minuti*  
  
1.  [Opzioni di condivisione del codice](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (xamarin.com). È consigliabile usare l'opzione relativa alle librerie di classi portabili, poiché offre il migliore supporto per l'uso delle sole API .NET che sono supportate in tutte le piattaforme di destinazione. Gran parte del codice per la logica di business si troverà nella libreria di classi Portabile, incluso l'accesso ai database, le chiamate alle API REST e le chiamate ai componenti di Xamarin portatili (vedere [Deeper Dive: I componenti di Xamarin](#components) alla fine di questo argomento). Anche il codice dell'interfaccia utente comune scritto con Xamarin.Forms può risiedere in una PCL.  
  
2.  (Facoltativo) [Case Study: Tasky](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/case_study-tasky/) (xamarin.com) vengono descritte alcune procedure consigliate per la progettazione e la struttura di un'app completa, come strutturare il progetto con una libreria di classi Portabile per il codice condiviso che separa i dati, l'accesso ai dati e il livello business.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Concetti di base: Livelli dell'interfaccia utente Xamarin Native e Xamarin.Forms  
 *10-40 minuti*  
  
 Xamarin offre due modi per creare eccezionali App native: Xamarin Native e xamarin. Forms.  
  
 Con Xamarin Native occorre scrivere codice separato per l'interfaccia utente per ogni piattaforma di destinazione: iOS, Android e Windows.  Con questo approccio è possibile accedere direttamente alle API specifiche della piattaforma e realizzare così un'esperienza dell'interfaccia utente personalizzata per ogni piattaforma.  È anche disponibile l'accesso completo alle finestre di progettazione e ai controlli nativi per ogni piattaforma, per facilitare la creazione dell'interfaccia utente corrispondente.  
  
 Xamarin.Forms offre un set di API generalizzato che consente di scrivere un livello di interfaccia utente condiviso per tutte le piattaforme in una libreria di classi portabile.  Xamarin.Forms prevede il rendering in controlli nativi in ciascuna piattaforma di destinazione per ottenere un aspetto originale.  Anziché usare una finestra di progettazione, con Xamarin.Forms l'interfaccia utente viene creata mediante C# e XAML.  
  
 Non è necessario decidere quale approccio adottare in anticipo. Le app possono essere implementate usando entrambi gli approcci in combinazione:  
  
- Usare Xamarin.Forms per creare schermate per uso generico che offrono un'interfaccia utente e funzionalità simili in tutte le piattaforme, come le schermate di accesso, i moduli di contatto e i risultati di ricerca.  
  
- Xamarin.Forms consente anche di usare un'ampia gamma di funzionalità di personalizzazione per adattare l'interfaccia utente a ogni piattaforma. È ad esempio possibile usare l'API OnPlatform, sia dal codice che da XAML, per creare una visualizzazione personalizzata, estendere un renderer esistente e creare un renderer personalizzato.  
  
- Se necessario, usare Xamarin Native per creare schermate che usano funzionalità dell'interfaccia utente univoche di ogni piattaforma, ad esempio una schermata che usa funzionalità native per l'acquisizione da fotocamera e la manipolazione delle immagini.  
  
  È consigliabile iniziare sempre con una soluzione Xamarin.Forms per impostare il codice dell'interfaccia utente condiviso tra le piattaforme e poi usare le funzionalità di personalizzazione per gli adeguamenti specifici della piattaforma. Se e quando è necessario creare schermate interamente specifiche della piattaforma, è possibile aggiungerle singolarmente tramite Xamarin Native.  
  
  Per altre informazioni:  
  
1.  [Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/) (xamarin.com) fornisce una breve panoramica e informazioni sui vantaggi e gli svantaggi di Xamarin.Forms rispetto ai livelli dell'interfaccia utente nativa (ovvero, Xamarin.iOS e Xamarin.Android).  
  
2.  I primi tre minuti del video di James Montemagno [xamarin. Forms: Native App iOS, Android e Windows con C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel 9, 13m3s) forniscono un'altra Panoramica ed è possibile continuare a guardare alcune demo.  
  
3.  (Facoltativo) [Introduzione a Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/introduction-to-xamarin-forms/) (xamarin.com)  
  
4.  (Facoltativo) Vedere alcuni esempi di come usare OnPlatform per la personalizzazione nella documentazione relativa alla [classe Device](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) (xamarin.com)  
  
5.  (Facoltativo) L'articolo dedicato alla [condivisione del codice dell'interfaccia utente tra piattaforme per dispositivi mobili diverse con Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) di Jason Smith (MSDN Magazine) presenta le varie opzioni di personalizzazione disponibili in Xamarin.Forms. Altri dettagli sono disponibili nell'articolo relativo alla [personalizzazione dei controlli per ogni piattaforma](http://developer.xamarin.com/guides/xamarin-forms/custom-renderer/) (xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Approfondimento: Debug con gli emulatori  
 *10-15 minuti*  
  
 Per eseguire il debug di app multipiattaforma senza dover usare un dispositivo fisico, saranno necessari gli strumenti seguenti:  
  
1.  **Emulatore Android.** A seconda della versione di Windows in uso, è consigliabile usare Visual Studio Emulator for Android di Microsoft o Xamarin Player, che offrono entrambi prestazioni elevate e supportano un'ampia gamma di funzionalità dei dispositivi:  
  
    -   **Computer Windows 8 e versioni successive:** È consigliabile usare di Microsoft [Visual Studio Emulator for Android](https://www.visualstudio.com/features/msft-android-emulator-vs.aspx), che viene installato con Visual Studio.  Il video dedicato a [Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (Channel 9, 5 minuti e 55 secondi) offre una panoramica e una dimostrazione.  
  
    -   **Windows 7 o versioni precedenti e Windows in esecuzione su Mac OS X**: usare [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player) (xamarin.com).  
  
2.  **Simulatore iOS di Apple.** Per altre informazioni, leggere l'[introduzione al simulatore iOS](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
3.  **Emulatore Windows Phone di Microsoft.** Per altre informazioni, leggere l' [Emulatore Windows Phone per Windows Phone 8](https://msdn.microsoft.com/library/dn632391.aspx).  
  
##  <a name="components"></a> Approfondimento: Componenti di Xamarin  
 *10 minuti*  
  
 Numerose funzionalità estese sono disponibili per le app Xamarin mediante i componenti di Xamarin. All'indirizzo [http://components.xamarin.com/](http://components.xamarin.com/) è disponibile per il download il catalogo completo, che include i componenti per controlli aggiuntivi dell'interfaccia utente e per l'autenticazione, oltre a un'ampia gamma di servizi cloud come Microsoft Azure e molto altro ancora.
