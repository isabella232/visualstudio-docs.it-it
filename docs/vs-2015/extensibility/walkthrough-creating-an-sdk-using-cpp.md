---
title: 'Procedura dettagliata: creazione di un SDK con C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202056"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Procedura dettagliata: creazione di un SDK con C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come creare un SDK di Math Library per C++ nativo, assemblare l'SDK come estensione di Visual Studio (VSIX) e quindi usarlo per creare un'app. La procedura dettagliata è divisa in questi passaggi:  
  
- [Per creare le librerie native e Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Per creare il progetto di estensione NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Per creare le librerie native e Windows Runtime  
  
1. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2. Nell'elenco dei modelli espandere **Visual C++**, **Windows Store**, quindi selezionare il modello **dll (app di Windows Store)** . Nella casella **nome** specificare `NativeMath` , quindi scegliere il pulsante **OK** .  
  
3. Aggiornare NativeMath. h in modo che corrisponda al codice seguente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Aggiornare NativeMath. cpp in modo che corrisponda al codice seguente:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. In **Esplora soluzioni**aprire il menu di scelta rapida per la **soluzione ' NativeMath '**, quindi scegliere **Aggiungi**, **nuovo progetto**.  
  
6. Nell'elenco dei modelli espandere **Visual C++**, quindi selezionare il modello di **componente Windows Runtime** . Nella casella **nome** specificare `NativeMathWRT` , quindi scegliere il pulsante **OK** .  
  
7. Aggiornare Class1. h in modo che corrisponda al codice seguente:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Aggiornare Class1. cpp in modo che corrisponda al codice seguente:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Per creare il progetto di estensione NativeMathVSIX  
  
1. In **Esplora soluzioni**aprire il menu di scelta rapida per la **soluzione ' NativeMath '**, quindi scegliere **Aggiungi**, **nuovo progetto**.  
  
2. Nell'elenco dei modelli espandere **Visual C#**, **Extensibility**e quindi selezionare **pacchetto VSIX**. Nella casella **nome** specificare **NativeMathVSIX**, quindi scegliere il pulsante **OK** .  
  
3. Quando viene visualizzata la finestra Progettazione manifesto VSIX, chiuderla.  
  
4. In **Esplora soluzioni**aprire il menu di scelta rapida per **source. Extension. vsixmanifest**, quindi scegliere **Visualizza codice**.  
  
5. Utilizzare il codice XML seguente per sostituire il codice XML esistente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **NativeMathVSIX** , quindi scegliere **Aggiungi**, **nuovo elemento**.  
  
7. Nell'elenco di **elementi di Visual C#** espandere **dati**, quindi selezionare **file XML**. Nella casella **nome** specificare `SDKManifest.xml` , quindi scegliere il pulsante **OK** .  
  
8. Utilizzare questo codice XML per sostituire il contenuto del file:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. In **Esplora soluzioni**, nel progetto **NativeMathVSIX** , creare questa struttura di cartelle:  
  
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
  
10. In **Esplora soluzioni**aprire il menu di scelta rapida per la **soluzione ' NativeMath '** e quindi scegliere **Apri cartella in Esplora file**.  
  
11. In **Esplora file**copiare \NativeMath\NativeMath.h, quindi in **Esplora soluzioni**, nel progetto **NativeMathVSIX** , incollarlo nella cartella \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Copiare \Debug\NativeMath\NativeMath.lib, quindi incollarlo nella cartella \DesignTime\Debug\x86\.  
  
     Copiare \Debug\NativeMath\NativeMath.dll e incollarlo nella cartella \Redist\Debug\x86\.  
  
     Copiare DebugNativeMathWRTNativeMathWRT.dll e incollarlo nella cartella RedistDebugx86.  
  
     Copiare DebugNativeMathWRTNativeMathWRT. winmd e incollarlo nella cartella ReferencesCommonConfigurationNeutral.  
  
     Copiare DebugNativeMathWRTNativeMathWRT. pri e incollarlo nella cartella ReferencesCommonConfigurationNeutral.  
  
12. Nella cartella \DesignTime\Debug\x86\ creare un file di testo denominato NativeMathSDK. props, quindi incollare il contenuto seguente:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Sulla barra dei menu scegliere **Visualizza**, **altre finestre**, **finestra Proprietà** (tastiera: premere il tasto F4).  
  
14. In **Esplora soluzioni**selezionare il file **NativeMathWRT. winmd** . Nella finestra **Proprietà** impostare la proprietà **azione di compilazione** su **contenuto**, quindi impostare la proprietà **Includi in VSIX** su **true**.  
  
     Ripetere questo processo per il file **SimpleMath. pri** .  
  
     Ripetere questo processo per il file **NativeMath. lib** .  
  
     Ripetere questo processo per il file **NativeMathSDK. props** .  
  
15. In **Esplora soluzioni**selezionare il file **NativeMath. h** . Nella finestra **Proprietà** modificare la proprietà **Includi in VSIX** su **true**.  
  
     Ripetere questo processo per il file di **NativeMath.dll** .  
  
     Ripetere questo processo per il file di **NativeMathWRT.dll** .  
  
     Ripetere questo processo per il file di **SDKManifest.xml** .  
  
16. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
17. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **NativeMathVSIX** , quindi scegliere **Apri cartella in Esplora file**.  
  
18. In **Esplora file**passare alla cartella \bin\debug\, quindi eseguire NativeMathVSIX. VSIX per avviare l'installazione.  
  
19. Scegliere il pulsante **Installa** , attendere il completamento dell'installazione, quindi riavviare Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi  
  
1. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2. Nell'elenco dei modelli espandere **Visual C++**, **Windows Store**, quindi selezionare **app vuota**. Nella casella **nome** specificare **NativeMathSDKSample**, quindi scegliere il pulsante **OK** .  
  
3. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **NativeMathSDKSample** , quindi scegliere **Aggiungi**, **riferimento**.  
  
4. Nella pagina proprietà **comuni**, **Framework e riferimenti** , nell'elenco dei tipi di riferimento, espandere **Windows**e quindi selezionare **estensioni**. Nel riquadro dei dettagli selezionare l'estensione **Math SDK nativa** , quindi scegliere il pulsante **Aggiungi nuovo riferimento** .  
  
5. Nella finestra di dialogo **Aggiungi riferimento** selezionare la casella di controllo **native Math SDK** , quindi scegliere il pulsante **OK** .  
  
6. Visualizzare le proprietà del progetto per NativeMathSDKSample.  
  
    Le proprietà definite in NativeMathSDK. props sono state applicate quando è stato aggiunto il riferimento. È possibile verificare questo problema esaminando la proprietà **directory di VC + +** delle proprietà di **configurazione**del progetto.  
  
7. In **Esplora soluzioni**aprire MainPage. XAML e quindi usare il codice XAML seguente per sostituirne il contenuto:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Aggiornare MainPage. XAML. h in modo che corrisponda al codice seguente:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Aggiornare MainPage. XAML. cpp in modo che corrisponda al codice seguente:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Premere il tasto F5 per eseguire l'app.  
  
11. Nell'app immettere due numeri, selezionare un'operazione, quindi scegliere il **=** pulsante.  
  
     Viene visualizzato il risultato corretto.  
  
    In questa procedura dettagliata è stato illustrato come creare e usare un SDK di estensione per chiamare una [!INCLUDE[wrt](../includes/wrt-md.md)] libreria e una libreria non [!INCLUDE[wrt](../includes/wrt-md.md)] .  
  
## <a name="next-steps"></a>Passaggi successivi  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: creazione di un SDK tramite C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creazione di un Software Development Kit](../extensibility/creating-a-software-development-kit.md)
