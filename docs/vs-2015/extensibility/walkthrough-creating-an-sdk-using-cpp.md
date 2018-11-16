---
title: 'Procedura dettagliata: Creazione di un SDK con C++ | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0932759213d064c3df717b7b6735c1201e62ce14
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773470"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Procedura dettagliata: creazione di un SDK con C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come creare una libreria C++ nativa math SDK, il SDK come un Visual Studio Extension (VSIX), pacchetto e quindi usarlo per creare un'app. La procedura dettagliata è suddivisa in questi passaggi:  
  
-   [Per creare il nativo e le librerie di Runtime di Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Per creare il progetto di estensione NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Per creare il nativo e le librerie di Runtime di Windows  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual C++**, **Windows Store**, quindi selezionare il **DLL (applicazioni Windows Store)** modello. Nel **nome** , specificare `NativeMath`, quindi scegliere il **OK** pulsante.  
  
3.  Aggiornare NativeMath.h affinché corrisponda al codice seguente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4.  Aggiornare NativeMath.cpp adattandola questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5.  In **Esplora soluzioni**, aprire il menu di scelta rapida **soluzione 'NativeMath'**, quindi scegliere **Add**, **nuovo progetto**.  
  
6.  Nell'elenco dei modelli, espandere **Visual C++**, quindi selezionare la **componente di Windows Runtime** modello. Nel **nome** , specificare `NativeMathWRT`, quindi scegliere il **OK** pulsante.  
  
7.  Aggiornare file Class1.h in modo che corrisponda a questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8.  Aggiornare Class1.cpp in modo che corrisponda a questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
##  <a name="createVSIX"></a> Per creare il progetto di estensione NativeMathVSIX  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida **soluzione 'NativeMath'**, quindi scegliere **Add**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual c#**, **Extensibility**, quindi selezionare **pacchetto VSIX**. Nel **nome** , specificare **NativeMathVSIX**, quindi scegliere il **OK** pulsante.  
  
3.  Quando viene visualizzata la finestra di progettazione del manifesto VSIX, chiuderla.  
  
4.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida **vsixmanifest**, quindi scegliere **Visualizza codice**.  
  
5.  Usare il codice XML seguente per sostituire il codice XML esistente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **NativeMathVSIX** del progetto e quindi scegliere **Add**, **nuovo elemento**.  
  
7.  Nell'elenco degli **elementi di Visual c#**, espandere **dati**, quindi selezionare **File XML**. Nel **nome** , specificare `SDKManifest.xml`, quindi scegliere il **OK** pulsante.  
  
8.  Usare questo codice XML per sostituire il contenuto del file:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. Nelle **Esplora soluzioni**, nella **NativeMathVSIX** progetto, creare questa struttura di cartelle:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. Nella **Esplora soluzioni**, aprire il menu di scelta rapida **soluzione 'NativeMath'**, quindi scegliere **Apri cartella in Esplora File**.  
  
11. Nella **Esplora File**, copiare \NativeMath\NativeMath.h e quindi in **Esplora soluzioni**, nel **NativeMathVSIX** del progetto, lo incollo il \DesignTime\ Cartella CommonConfiguration\Neutral\Include\.  
  
     Copiare \Debug\NativeMath\NativeMath.lib e quindi incollarlo nella cartella \DesignTime\Debug\x86\.  
  
     Copiare \Debug\NativeMath\NativeMath.dll e incollarlo nella cartella \Redist\Debug\x86\.  
  
     Copiare DebugNativeMathWRTNativeMathWRT.dll e incollarlo nella cartella RedistDebugx86.  
  
     Copiare DebugNativeMathWRTNativeMathWRT.winmd e incollarlo nella cartella ReferencesCommonConfigurationNeutral.  
  
     Copiare DebugNativeMathWRTNativeMathWRT.pri e incollarlo nella cartella ReferencesCommonConfigurationNeutral.  
  
12. Nella cartella \DesignTime\Debug\x86\, creare un file di testo denominato NativeMathSDK.props e quindi incollare il contenuto seguente in esso:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Nella barra dei menu, scegliere **View**, **Other Windows**, **finestra proprietà** (tastiera: premere il tasto F4).  
  
14. Nelle **Esplora soluzioni**, selezionare la **NativeMathWRT.winmd** file. Nel **delle proprietà** finestra Modifica il **azione di compilazione** proprietà **contenuto**e quindi modificare il **Includi in VSIX** proprietà  **True**.  
  
     Ripetere questo processo per il **SimpleMath.pri** file.  
  
     Ripetere questo processo per il **NativeMath.Lib** file.  
  
     Ripetere questo processo per il **NativeMathSDK.props** file.  
  
15. Nelle **Esplora soluzioni**, selezionare la **NativeMath.h** file. Nel **delle proprietà** finestra Modifica il **Includi in VSIX** proprietà **True**.  
  
     Ripetere questo processo per il **NativeMath.dll** file.  
  
     Ripetere questo processo per il **NativeMathWRT.dll** file.  
  
     Ripetere questo processo per il **Sdkmanifest** file.  
  
16. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
17. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **NativeMathVSIX** del progetto e quindi scegliere **Apri cartella in Esplora File**.  
  
18. Nelle **Esplora File**, passare alla cartella \bin\Debug\ e quindi eseguire NativeMathVSIX.vsix per iniziare l'installazione.  
  
19. Scegliere il **installare** pulsante, attendere il completamento dell'installazione e quindi riavviare Visual Studio.  
  
##  <a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi  
  
1. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2. Nell'elenco dei modelli, espandere **Visual C++**, **Windows Store**, quindi selezionare **applicazione vuota**. Nel **nome** , specificare **NativeMathSDKSample**, quindi scegliere il **OK** pulsante.  
  
3. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **NativeMathSDKSample** del progetto e quindi scegliere **Add**, **riferimento**.  
  
4. Nel **proprietà comuni**, **Framework e riferimenti** pagina delle proprietà, nell'elenco dei tipi riferimento, espandere **Windows**, quindi selezionare **estensioni** . Nel riquadro dei dettagli selezionare il **SDK nativo Math** estensione, quindi scegliere il **Aggiungi nuovo riferimento** pulsante.  
  
5. Nel **Aggiungi riferimento** finestra di dialogo, seleziona la **SDK nativo Math** casella di controllo e quindi scegliere il **OK** pulsante.  
  
6. Visualizzare le proprietà del progetto per NativeMathSDKSample.  
  
    Le proprietà definite in NativeMathSDK.props sono state applicate quando è stato aggiunto il riferimento. È possibile verificarlo esaminando i **directory di VC + +** proprietà del progetto **delle proprietà di configurazione**.  
  
7. Nelle **Esplora soluzioni**, aprire MainPage. XAML e quindi usare il seguente XAML per sostituire il contenuto:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Aggiornare MainPage in modo che corrisponda a questo codice:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Aggiornare MainPage.xaml.cpp adattandola questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Premere il tasto F5 per eseguire l'app.  
  
11. Nell'app, immettere tutti i due numeri, selezionare un'operazione e quindi scegliere il **=** pulsante.  
  
     Viene visualizzato il risultato corretto.  
  
    Questa procedura dettagliata ha illustrato come creare e usare un SDK di estensione per chiamare in un' [!INCLUDE[wrt](../includes/wrt-md.md)] libreria e non -[!INCLUDE[wrt](../includes/wrt-md.md)] libreria.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un SDK tramite c# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creazione di un Software Development Kit](../extensibility/creating-a-software-development-kit.md)

