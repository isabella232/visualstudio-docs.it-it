---
title: 'Procedura dettagliata: Creazione di un SDK con C++ | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2a0db4f34315f9e0eb4a5627cdc286a43a904a34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917605"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Procedura dettagliata: Creare un SDK con C++
Questa procedura dettagliata illustra come creare una libreria C++ nativa math SDK, il SDK come un Visual Studio Extension (VSIX), pacchetto e quindi usarlo per creare un'app. La procedura dettagliata è suddivisa in questi passaggi:  
  
-   [Per creare il nativo e le librerie di Runtime di Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Per creare il progetto di estensione NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Per creare il nativo e le librerie di Runtime di Windows  
  
1.  Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual C++** > **Windows Universal**, quindi selezionare il **DLL (app di Windows universale)** modello. Nel **nome** , specificare `NativeMath`, quindi scegliere il **OK** pulsante.  
  
3.  Update *NativeMath.h* in modo che corrisponda il codice seguente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Update *NativeMath.cpp* in modo che corrispondano questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  In **Esplora soluzioni**, aprire il menu di scelta rapida **soluzione 'NativeMath'**, quindi scegliere **Add** > **nuovo progetto**.  
  
6.  Nell'elenco dei modelli, espandere **Visual C++**, quindi selezionare la **componente di Windows Runtime** modello. Nel **nome** , specificare `NativeMathWRT`, quindi scegliere il **OK** pulsante.  
  
7.  Update *Class1.h* in modo che corrispondano questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Update *Class1.cpp* in modo che corrispondano questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Nella barra dei menu scegliere **Compila** > **Compila soluzione**.  
  
##  <a name="createVSIX"></a> Per creare il progetto di estensione NativeMathVSIX  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida **soluzione 'NativeMath'**, quindi scegliere **Add** > **nuovo progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual c#** > **Extensibility**, quindi selezionare **progetto VSIX**. Nel **nome** , specificare **NativeMathVSIX**, quindi scegliere il **OK** pulsante.
  
3.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida **vsixmanifest**, quindi scegliere **Visualizza codice**.  
  
4.  Usare il codice XML seguente per sostituire il codice XML esistente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **NativeMathVSIX** del progetto e quindi scegliere **Add** > **nuovo elemento**.  
  
6.  Nell'elenco degli **elementi di Visual c#**, espandere **dati**, quindi selezionare **File XML**. Nel **nome** , specificare `SDKManifest.xml`, quindi scegliere il **OK** pulsante.  
  
7.  Usare questo codice XML per sostituire il contenuto del file:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. Nelle **Esplora soluzioni**, sotto il **NativeMathVSIX** progetto, creare questa struttura di cartelle:  
  
    ```xml  
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
  
9. Nella **Esplora soluzioni**, aprire il menu di scelta rapida **soluzione 'NativeMath'**, quindi scegliere **Apri cartella in Esplora File**.  
  
10. Nella **Esplora File**, copia *$SolutionRoot$\NativeMath\NativeMath.h*e quindi in **Esplora soluzioni**, sotto il **NativeMathVSIX**del progetto, incollo qui il *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  cartella.  
  
     Copia *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*e quindi incollarlo nella *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  cartella.  
  
     Copia *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* e incollarlo nel *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  cartella.  
  
     Copia *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* e incollarlo nel *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* cartella.  
     Copia *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* e incollarlo nel *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* cartella.  
  
     Copia *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* e incollarlo nel *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* cartella.  
  
11. Nel *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  cartella, creare un file di testo denominato *NativeMathSDK.props*e quindi incollare il contenuto seguente in esso:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. Nella barra dei menu, scegliere **View** > **Other Windows** > **finestra proprietà** (tastiera: Scegliere il **F4** key).  
  
13. Nelle **Esplora soluzioni**, selezionare la **NativeMathWRT.winmd** file. Nel **delle proprietà** finestra Modifica il **azione di compilazione** proprietà **contenuto**e quindi modificare il **Includi in VSIX** proprietà  **True**.  
  
     Ripetere questo processo per il **NativeMath.h** file.  
  
     Ripetere questo processo per il **NativeMathWRT.pri** file.  
  
     Ripetere questo processo per il **NativeMath.Lib** file.  
  
     Ripetere questo processo per il **NativeMathSDK.props** file.  
  
14. Nelle **Esplora soluzioni**, selezionare la **NativeMath.h** file. Nel **delle proprietà** finestra Modifica il **Includi in VSIX** proprietà **True**.  
  
     Ripetere questo processo per il **NativeMath.dll** file.  
  
     Ripetere questo processo per il **NativeMathWRT.dll** file.  
  
     Ripetere questo processo per il **Sdkmanifest** file.  
  
15. Nella barra dei menu scegliere **Compila** > **Compila soluzione**.  
  
16. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **NativeMathVSIX** del progetto e quindi scegliere **Apri cartella in Esplora File**.  
  
17. Nelle **Esplora File**, passare al *$SolutionRoot$ \NativeMathVSIX\bin\Debug* cartella e quindi eseguire *NativeMathVSIX.vsix* per avviare l'installazione.  
  
18. Scegliere il **installare** pulsante, attendere il completamento dell'installazione e quindi avviare Visual Studio.  
  
##  <a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi  
  
1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.  
  
2. Nell'elenco dei modelli, espandere **Visual C++** > **Windows Universal** e quindi selezionare **App vuota**. Nel **nome** , specificare **NativeMathSDKSample**, quindi scegliere il **OK** pulsante.  
  
3. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **NativeMathSDKSample** del progetto e quindi scegliere **Add** > **riferimento**.  
  
4. Nel **Aggiungi riferimento** finestra di dialogo, nell'elenco dei tipi riferimento, espandere **Windows Universal**e quindi selezionare **estensioni**. Selezionare infine il **SDK nativo Math** casella di controllo e quindi scegliere il **OK** pulsante.
  
5. Visualizzare le proprietà del progetto per NativeMathSDKSample.  
  
    Le proprietà definite in *NativeMathSDK.props* sono state applicate quando è stato aggiunto il riferimento. È possibile verificare le proprietà sono state applicate esaminando il **directory di VC + +** proprietà del progetto **delle proprietà di configurazione**.  
  
6. Nelle **Esplora soluzioni**aprire **MainPage. XAML**e quindi usare il seguente XAML per sostituire il contenuto:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7. Update *MainPage* in modo che corrispondano questo codice:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Update *MainPage.xaml.cpp* in modo che corrispondano questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Scegliere il **F5** per eseguire l'app.  
  
10. Nell'app, immettere tutti i due numeri, selezionare un'operazione e quindi scegliere il **=** pulsante.  
  
     Viene visualizzato il risultato corretto.  
  
    Questa procedura dettagliata ha illustrato come creare e usare un SDK di estensione per chiamare in un' [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] libreria e non -[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] libreria.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creare un SDK tramite C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creare un software development kit](../extensibility/creating-a-software-development-kit.md)
