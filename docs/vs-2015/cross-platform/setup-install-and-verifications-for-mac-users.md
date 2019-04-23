---
title: Configurazione, installazione e verifiche per gli utenti Mac | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 54297754fcc85484a90e25686b0fd14aa7841946
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116004"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Configurazione, installazione e verifiche per gli utenti Mac
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento è destinato agli sviluppatori che lavorano principalmente su un Mac e che useranno facoltativamente Visual Studio in una macchina virtuale Windows sul Mac. Gli sviluppatori che lavorano principalmente su un computer Windows e devono impostare un Mac secondario per attività di sviluppo destinate a iOS possono vedere l'argomento [Configurazione e installazione](../cross-platform/setup-and-install.md) principale.  
  
 Per usare Xamarin su un Mac, è necessario quanto segue:  
  
- Un account Xamarin. Passare a [ https://www.xamarin.com/ ](https://www.xamarin.com/) e fare clic su **Accedi** nell'angolo in alto a destra della pagina, quindi fare clic su **creare un nuovo account** nella pagina visualizzata. Selezionare un indirizzo di posta elettronica e una password per l'account Xamarin.  
  
- Un Mac con OSX Yosemite (10.10) o versione successiva e con Xcode 7 e Xamarin 4 installati.  
  
- Una delle configurazioni seguenti:  
  
  - **Per esecuzione Xamarin Studio direttamente nel Mac:** Xamarin Studio è l'ambiente di sviluppo di Xamarin che supporta la creazione delle App Android, iOS e Windows usando C#.  Per una rapida panoramica di Xamarin Studio, vedere i [cenni preliminari su Xamarin Studio](https://xamarin.com/studio) (xamarin.com).  
  
  - **Se nel Mac è già configurato Parallels o VMWare:** eseguire Windows con Visual Studio 2015 e Xamarin 4 in Parallels o VMWare.  Con questa configurazione, Xamarin è un'estensione installata con Visual Studio che offre la possibilità di usare Visual Studio come ambiente di sviluppo per la creazione di app Android, iOS e Windows Phone tramite C#.  Si noti che è possibile ottenere una sottoscrizione gratuita di Parallels per 3 mesi nell'ambito del programma Visual Studio Developer Essentials. Vedere la pagina relativa al fatto che [Microsoft Visual Studio Developer Essentials includerà Parallels Desktop Pro e l'accesso a Parallels](http://blog.parallels.com/blog/2015/11/18/visual-studio-dev-essentials/) (blog di Parallels).  
  
  In questo argomento vengono fornite istruzioni per tali requisiti.  Mentre il processo di installazione è in esecuzione, è possibile esaminare l'argomento [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) per leggere e guardare il materiale di riferimento necessario.  
  
  **Contenuto dell'argomento:**  
  
- [Installazione in ambiente Mac (ID Apple, Xcode e Xamarin)](#mac)  
  
- [Installazione di Windows in Parallels (Visual Studio e Xamarin)](#windows)  
  
- [Verificare l'ambiente](#verify)  
  
## <a name="mac"></a> Installazione di Mac (ID Apple, Xcode e Xamarin)  
  
1. Creare un ID Apple gratuito in [ID Apple](https://appleid.apple.com/) , se non ne è già disponibile uno. Questo è necessario per l'installazione e la firma in Xcode.  
  
2. Scaricare e installare Xcode da [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/).  
  
3. Scaricare e installare Xamarin seguendo le istruzioni nella pagina relativa a [installazione e configurazione di Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4. Dopo aver completato l'installazione di Xamarin nei computer Windows e Mac, seguire le istruzioni nella pagina relativa alla [connessione al Mac tramite XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com) in modo da usare iOS e il Mac da Visual Studio nel computer Windows.  
  
## <a name="windows"></a> Installazione di Windows in Parallels (Visual Studio e Xamarin)  
  
1. Usando il desktop Windows che è stato configurato in Parallels/VMWare, [scaricare e avviare il programma di installazione di qualsiasi edizione di Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional o Enterprise). Visual Studio Community 2015 è l'edizione gratuita. Le edizioni Professional ed Enterprise possono essere usate per un periodo di valutazione di 30 giorni.  
  
2. Nel programma di installazione selezionare l'installazione **personalizzata** :  
  
     ![Scelta dell'opzione Personalizzata nell'installazione di Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "Cross-Plat Xamarin Setup 1")  
  
3. Selezionare/deselezionare le caselle seguenti:  
  
    1. Selezionare **Sviluppo di app per dispositivi mobili multipiattaforma > C#/.NET (Xamarin)**. In questo modo verranno selezionati automaticamente anche vari strumenti Android in Strumenti comuni e Software Development Kit.  
  
         ![Selezione dell'opzione Xamarin in Sviluppo di app per dispositivi mobili multipiattaforma](../cross-platform/media/cross-plat-xamarin-setup-2.png "Cross-Plat Xamarin Setup 2")  
  
    2. Deselezionare **Sviluppo di app per dispositivi mobili multipiattaforma > Microsoft Visual Studio Emulator for Android**.  
  
4. Fare clic sul pulsante Installa e attendere l'esecuzione del processo. Anche in questo caso, l'operazione richiederà un certo tempo. Nel frattempo è possibile procedere con questo argomento e passare a [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Al termine dell'installazione, avviare Visual Studio e accedere con l'account Microsoft se viene richiesto (si tratta dello stesso account che viene usato per Windows). Verificare quindi la disponibilità di aggiornamenti per Xamarin tramite **Strumenti > Opzioni > Xamarin** o **Strumenti > Opzioni > Xamarin > Altro**, in cui è disponibile un collegamento **Verifica ora**:  
  
     ![Controllo degli aggiornamenti di Xamarin nelle opzioni di Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "Cross-Plat Xamarin Setup 3")  
  
    > [!NOTE]
    >  Assicurarsi di aggiornare Xamarin alla versione 4.0.3.214 o successiva per evitare problemi con le licenze precedenti di Xamarin.  Se si tenta di verificare la disponibilità di aggiornamenti e viene visualizzato un errore relativo agli strumenti di compilazione Microsoft, vedere il thread nei [forum di Xamarin](http://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015).
  
6. Dopo aver completato l'installazione di Xamarin nei computer Windows e Mac, seguire le istruzioni nella pagina relativa alla [connessione al Mac tramite XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com) in modo da usare iOS da Visual Studio.  
  
## <a name="verify"></a> Verificare l'ambiente  
 Al termine dei programmi di installazione, dedicare alcuni minuti per verificare che tutto sia pronto per le attività di sviluppo con Xamarin.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 In primo luogo, verificare che, quando si visitano i collegamenti disponibili, sia selezionato **Xamarin Studio** nell'angolo superiore destro, in modo da visualizzare la versione corretta della documentazione di Xamarin:  
  
 ![Selezione di Xamarin Studio per visualizzare la documentazione corretta in Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. Convalidare la creazione di un progetto Android seguendo le istruzioni nella pagina relativa alla [creazione di un progetto Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).  
  
2. Convalidare il debug in Android Player tramite la pagina relativa all'[integrazione con la documentazione di Xamarin Studio in Android Player](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (xamarin.com).  
  
   **iOS**  
  
3. Convalidare la creazione di un progetto iOS seguendo le istruzioni nella pagina relativa alla [creazione di un progetto iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).  
  
4. Convalidare il debug nel simulatore iOS tramite la [documentazione relativa al debug nel simulatore](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com).  
  
### <a name="visual-studio"></a>Visual Studio  
 In primo luogo, verificare che, quando si visitano i collegamenti disponibili, sia selezionato **Visual Studio** nell'angolo superiore destro, in modo da visualizzare la versione corretta della documentazione di Xamarin:  
  
 ![Selezione di Visual Studio per visualizzare la documentazione corretta in Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 Accedere inoltre all'account Xamarin tramite **Strumenti > Account Xamarin**.  
  
 **Android**  
  
1. Convalidare la creazione di un progetto Android seguendo le istruzioni nella pagina relativa alla [creazione di un progetto Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).  
  
2. Convalidare la finestra di progettazione Android: nel progetto Android in Esplora soluzioni aprire il file **Risorse > Layout > Main.axml**.  
  
   - Se viene visualizzato l'errore "The installed Android SDK is too old" (Android SDK installato è troppo vecchio), fare clic su **Open Android SDK** (Apri Android SDK) nel messaggio e selezionare la versione dell'SDK più recente disponibile. Si noti che è necessario eseguire Visual Studio come amministratore per aggiornare l'SDK.  
  
3. Verificare che sia possibile connettersi da Visual Studio all'emulatore installato nel Mac.  Come risultato, Xamarin Player sarà visualizzato nell'elenco degli emulatori che è possibile selezionare in Visual Studio per il debug.  A tale scopo, seguire le istruzioni nella pagina relativa alla [connessione di Visual Studio a Xamarin Android Player](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/android-player-with-visual-studio-in-vm/) (xamarin.com).  
  
   **iOS**  
  
4. Assicurarsi che il Mac sia disponibile in rete e associato a Visual Studio, come descritto nella pagina relativa alla [connessione al Mac tramite XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com).  
  
5. Convalidare la creazione di un progetto iOS seguendo le istruzioni nella pagina relativa alla [creazione di un progetto iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).  
  
6. Convalidare la finestra di progettazione dello storyboard: nel progetto iOS in Esplora soluzioni aprire il file **MainStoryboard.storyboard** . In questo caso, Visual Studio ospita la finestra di progettazione, che è in esecuzione in remoto sul Mac.  
  
7. Convalidare la compilazione e il debug:  
  
   1. Fare clic con il pulsante destro del mouse sul progetto iOS in Esplora soluzioni e scegliere **Imposta come progetto di avvio**.  
  
   2. Selezionare la destinazione **iPhoneSimulator** dall'elenco a discesa di compilazione di Visual Studio, come illustrato di seguito. Se non è elencato alcun simulatore, avviare Xcode nel Mac, selezionare **Xcode->Preferences** e fare clic su **Download**. In **Components** dovrebbero essere visualizzate le versioni del simulatore disponibili per il download. Ulteriori istruzioni per il debug sono disponibili nella pagina relativa al [debug](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) di Xamarin (xamarin.com).  
  
        ![Selezione della destinazione di compilazione di iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")  
  
   3. Selezionare una destinazione iPhone dall'elenco a discesa di debug di Visual Studio, come illustrato di seguito, e avviare il debugger premendo F5. Verrà avviato il simulatore nel Mac, in cui è possibile interagire con l'app, mentre viene eseguito il debug in Visual Studio.  
  
        ![Selezione di una destinazione di debug iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")
