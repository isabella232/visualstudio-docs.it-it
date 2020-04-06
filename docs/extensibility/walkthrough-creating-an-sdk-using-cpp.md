---
title: 'Procedura dettagliata: creazione di un SDK utilizzando C . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697638"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Procedura dettagliata: Creazione di un SDK con C
In questa procedura dettagliata viene illustrato come creare un SDK di libreria matematica c'è un nativo, creare un pacchetto dell'SDK come estensione di Visual Studio (VSIX) e quindi usarlo per creare un'app. La procedura dettagliata è suddivisa in questi passaggi:The walkthrough is divided into these steps:

- [Per creare le librerie native e Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Per creare il progetto di estensione NativeMathVSIXTo create the NativeMathVSIX extension project](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Per creare un'app di esempio che usa la libreria di classiTo create a sample app that uses the class library](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Per creare le librerie native e Windows Runtime

1. Nella barra dei menu scegliere **File** > **Nuovo** > **progetto**.

2. Nell'elenco dei modelli, espandere **Visual C,** > **Windows Universale**, quindi selezionare il modello DLL **(App universali** di Windows). Nella casella **Nome** `NativeMath`specificare , quindi scegliere **ok.**

3. Aggiornare *NativeMath.h* in modo che corrisponda al codice seguente.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Aggiornare *NativeMath.cpp* in modo che corrisponda a questo codice:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. In **Esplora soluzioni**aprire il menu di scelta rapida per **Soluzione 'NativeMath'**, quindi scegliere **Aggiungi** > **nuovo progetto**.

6. Nell'elenco dei modelli, espandere **Visual C,** quindi selezionare il modello **Componente Windows Runtime.** Nella casella **Nome** `NativeMathWRT`specificare , quindi scegliere **ok.**

7. Aggiornare *Class1.h* in modo che corrisponda a questo codice:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Aggiorna *Class1.cpp* in modo che corrisponda a questo codice:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Nella barra dei menu scegliere **Compila** > soluzione di**compilazione**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Per creare il progetto di estensione NativeMathVSIXTo create the NativeMathVSIX extension project

1. In **Esplora soluzioni**aprire il menu di scelta rapida per **Soluzione 'NativeMath'**, quindi scegliere **Aggiungi** > **nuovo progetto**.

2. Nell'elenco dei modelli , espandere**Estensibilità** **di Visual C** > , quindi selezionare **Progetto VSIX**. Nella casella **Nome** specificare **NativeMathVSIX**, quindi scegliere **OK** .

3. In **Esplora soluzioni**aprire il menu di scelta rapida per **source.extension.vsixmanifest**, quindi scegliere **Visualizza codice**.

4. Utilizzare il codice XML seguente per sostituire il codice XML esistente.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **NativeMathVSIX,** quindi scegliere **Aggiungi** > **nuovo elemento**.

6. Nell'elenco degli elementi di **Visual C,** espandere **Dati**, quindi selezionare **File XML**. Nella casella **Nome** `SDKManifest.xml`specificare , quindi scegliere **ok.**

7. Utilizzare questo codice XML per sostituire il contenuto del file:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. In **Esplora soluzioni**, nel progetto **NativeMathVSIX,** creare la struttura di cartelle seguente:In Solution Explorer , under the NativeMathVSIX project, create this folder structure:

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

9. In **Esplora soluzioni**aprire il menu di scelta rapida per **soluzione 'NativeMath'**, quindi scegliere **Apri cartella in Esplora file**.

10. In **Esplora file**, copiare $SolutionRoot , , *$SolutionRoot\\ * **Solution Explorer** *,*, , **NativeMathVSIX** , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , ,

     Copiare $SolutionRoot , *Debug , NativeMath , NativeMath.lib*, quindi incollarlo nella cartella *$SolutionRoot\\ * .

     Copiare *$SolutionRoot, Debug, NativeMath, NativeMath.dll* e incollarlo nella cartella *$SolutionRoot\\ * .

     Copiare *$SolutionRoot'oalt.id/debug/NativeMathWRT.dll* e incollarlo nella cartella *$SolutionRoot* .
     Copiare il file *$SolutionRoot, Debug, NativeMathWRT, NativeMathWRT.winmd* e incollarlo nella cartella *$SolutionRoot* .

     Copiare il file $SolutionRoot, debug, *NativeMathWRT, NativeMathWRT.pri* e incollarlo nella cartella *$SolutionRoot* .

11. Nella cartella $SolutionRoot , *nativeMathVSIX , DesignTime\\ Debug , x86* , creare un file di testo denominato *NativeMathSDK.props*e quindi incollare il contenuto seguente in esso:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Nella barra dei menu scegliere **Visualizza** > altra**finestra delle proprietà** di**Windows** > (tastiera: scegliere il tasto **F4).**

13. In **Esplora soluzioni**selezionare il file **NativeMathWRT.winmd.** Nella finestra **Proprietà** modificare la proprietà Operazione di **compilazione** in **Contenuto**, quindi la proprietà **Includi in VSIX** in **True**.

     Ripetere questo processo per il file **NativeMath.h.**

     Ripetere questo processo per il file **NativeMathWRT.pri.**

     Ripetere questo processo per il file **NativeMath.Lib.**

     Ripetere questo processo per il file **NativeMathSDK.props.**

14. In **Esplora soluzioni**selezionare il file **NativeMath.h.** Nella finestra **Proprietà** impostare la proprietà **Includi in VSIX** su **True**.

     Ripetere questo processo per il file **NativeMath.dll.**

     Ripetere questo processo per il file **NativeMathWRT.dll.**

     Ripetere questo processo per il file **SDKManifest.xml.**

15. Nella barra dei menu scegliere **Compila** > soluzione di**compilazione**.

16. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **NativeMathVSIX,** quindi scegliere **Apri cartella in Esplora file**.

17. In **Esplora file**, passare alla cartella *$SolutionRoot* , quindi eseguire *NativeMathVSIX.vsix* per avviare l'installazione.

18. Scegliere **il** installa pulsante, attendere il completamento dell'installazione e quindi aprire Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Per creare un'app di esempio che usa la libreria di classiTo create a sample app that uses the class library

1. Nella barra dei menu scegliere **File** > **Nuovo** > **progetto**.

2. Nell'elenco dei modelli, espandere **Visual C,** > **Windows Universal** , quindi selezionare Applicazione **vuota**. Nella casella **Nome** specificare **NativeMathSDKSample**, quindi scegliere **OK** .

3. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **NativeMathSDKSample,** quindi scegliere **Aggiungi** > **riferimento**.

4. Nell'elenco dei tipi di riferimento della finestra di dialogo **Aggiungi riferimento** espandere **Windows universale**, quindi selezionare **Estensioni**. Infine, selezionare la casella di controllo **SDK matematica nativa** e quindi scegliere il **OK** pulsante.

5. Visualizzare le proprietà del progetto per NativeMathSDKSample.

    Le proprietà definite in *NativeMathSDK.props* sono state applicate al momento dell'aggiunta del riferimento. È possibile verificare che le proprietà siano state applicate esaminando la proprietà **Directory DI VC,** delle proprietà di **configurazione**del progetto.

6. In **Esplora soluzioni**aprire **MainPage.xaml**, quindi utilizzare il codice XAML seguente per sostituirne il contenuto:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Aggiornare Mainpage.xaml.h in modo che corrisponda a questo codice:Update *Mainpage.xaml.h* to match this code:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Aggiornare MainPage.xaml.cpp in modo che corrisponda a questo codice:Update *MainPage.xaml.cpp* to match this code:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Scegliere il **tasto F5** per eseguire l'app.

10. Nell'app immettere due numeri qualsiasi, selezionare **=** un'operazione e quindi scegliere il pulsante .

     Viene visualizzato il risultato corretto.

    In questa procedura dettagliata è stato illustrato come [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] creare e[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] usare un SDK di estensione per chiamare in una libreria e una non libreria.

## <a name="next-steps"></a>Passaggi successivi

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Creazione di un SDK con C .NET o Visual BasicWalkthrough: Create an SDK using C 'amp-Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Creare un kit di sviluppo software](../extensibility/creating-a-software-development-kit.md)
