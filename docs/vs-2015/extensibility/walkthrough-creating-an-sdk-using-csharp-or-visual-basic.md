---
title: 'Procedura dettagliata: creazione di un SDK tramite C# o Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77558212"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Procedura dettagliata: creazione di un SDK con C# o Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata verrà illustrato come creare un semplice SDK della libreria Math usando Visual C# e come creare il pacchetto dell'SDK come estensione di Visual Studio (VSIX). Verranno completate le procedure seguenti:  
  
- [Per creare il componente Windows Runtime SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [Per creare il progetto di estensione SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Per creare il componente Windows Runtime SimpleMath  
  
1. Sulla barra dei menu scegliere **file**, **nuovo**, **nuovo progetto**.  
  
2. Nell'elenco dei modelli espandere **Visual C#** o **Visual Basic**, scegliere il nodo **Windows Store** , quindi scegliere il modello **Windows Runtime componente** .  
  
3. Nella casella **nome** specificare **SimpleMath**, quindi scegliere il pulsante **OK** .  
  
4. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto **SimpleMath** , quindi scegliere **proprietà**.  
  
5. Rinominare **Class1.cs** in **Arithmetic.cs** e aggiornarlo in modo che corrisponda al codice seguente:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **soluzione ' SimpleMath '** , quindi scegliere **Configuration Manager**.  
  
     Verrà visualizzata la finestra di dialogo **Configuration Manager** .  
  
7. Nell'elenco **Configurazione soluzione attiva** scegliere **versione**.  
  
8. Nella colonna **configurazione** verificare che la riga **SimpleMath** sia impostata su **rilascia**, quindi scegliere il pulsante **Chiudi** per accettare la modifica.  
  
    > [!IMPORTANT]
    > L'SDK per il componente SimpleMath include una sola configurazione. Questa configurazione deve essere la build di rilascio o le app che usano il componente non passeranno la certificazione per il [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] .  
  
9. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto **SimpleMath** , quindi scegliere **Compila**.  
  
## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Per creare il progetto di estensione SimpleMathVSIX  
  
1. Nel menu di scelta rapida per il nodo della **soluzione ' SimpleMath '** scegliere **Aggiungi**, **nuovo progetto**.  
  
2. Nell'elenco dei modelli espandere **Visual C#** o **Visual Basic**, scegliere il nodo **estensibilità** , quindi scegliere il modello di **progetto VSIX** .  
  
3. Nella casella **nome** specificare **SimpleMathVSIX**, quindi scegliere il pulsante **OK** .  
  
4. In **Esplora soluzioni**scegliere l'elemento **source. Extension. vsixmanifest** .  
  
5. Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
6. Sostituire il codice XML esistente con il codice XML seguente:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. In **Esplora soluzioni**scegliere il progetto **SimpleMathVSIX** .  
  
8. Sulla barra dei menu scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
9. Nell'elenco di **elementi comuni**espandere **dati**, quindi scegliere **file XML**.  
  
10. Nella casella **nome** specificare `SDKManifest.xml` , quindi scegliere il pulsante **Aggiungi** .  
  
11. In **Esplora soluzioni**aprire il menu di scelta rapida per `SDKManifest.xml` , scegliere **proprietà**e quindi modificare il valore della proprietà **Includi in VSIX** su **true**.  
  
12. Sostituisci il contenuto del file con il codice XML riportato di seguito:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **SimpleMathVSIX** , scegliere **Aggiungi**, quindi scegliere **nuova cartella**.  
  
14. Rinominare la cartella in `references` .  
  
15. Aprire il menu di scelta rapida per la cartella **riferimenti** , scegliere **Aggiungi**, quindi scegliere **nuova cartella**.  
  
16. Rinominare la sottocartella in `commonconfiguration` , creare una sottocartella al suo interno e denominare la sottocartella `neutral` .  
  
17. Ripetere i quattro passaggi precedenti, in questo caso rinominare la prima cartella in `redist` .  
  
     Il progetto ora contiene la struttura di cartelle seguente:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **SimpleMath** , quindi scegliere **Apri cartella in Esplora file**.  
  
19. In **Esplora file**passare alla cartella bin\release, aprire il menu di scelta rapida per il file SimpleMath. winmd, quindi scegliere **copia**.  
  
20. In **Esplora soluzioni**incollare il file nella cartella references\commonconfiguration\neutral del progetto **SimpleMathVSIX** .  
  
21. Ripetere il passaggio precedente, incollando il file SimpleMath. pri nella cartella redist\commonconfiguration\neutral del progetto **SimpleMathVSIX** .  
  
22. In **Esplora soluzioni**scegliere **SimpleMath. winmd**.  
  
23. Sulla barra dei menu scegliere **Visualizza**, **Proprietà** (tastiera: premere il tasto F4).  
  
24. Nella finestra **Proprietà** impostare la proprietà **azione di compilazione** su **contenuto**, quindi impostare la proprietà **Includi in VSIX** su **true**.  
  
25. In **Esplora soluzioni**ripetere questo processo per **SimpleMath. pri**.  
  
26. In **Esplora soluzioni**scegliere il progetto **SimpleMathVSIX** .  
  
27. Sulla barra dei menu scegliere **Compila**, **Compila SimpleMathVSIX**.  
  
28. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **SimpleMathVSIX** , quindi scegliere **Apri cartella in Esplora file**.  
  
29. In **Esplora file**passare alla cartella \bin\release, quindi eseguire SimpleMathVSIX. VSIX per installarlo.  
  
30. Scegliere il pulsante **Installa** , attendere il completamento dell'installazione, quindi riavviare Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi  
  
1. Sulla barra dei menu scegliere **file**, **nuovo**, **nuovo progetto**.  
  
2. Nell'elenco dei modelli espandere **Visual C#** o **Visual Basic**, quindi scegliere il nodo **Windows Store** .  
  
3. Scegliere il modello **applicazione vuota** , denominare il progetto **ArithmeticUI**, quindi scegliere il pulsante **OK** .  
  
4. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ArithmeticUI** , quindi scegliere **Aggiungi**, **riferimento**.  
  
5. Nell'elenco dei tipi di riferimento espandere **Windows**, quindi scegliere **estensioni**.  
  
6. Nel riquadro dei dettagli scegliere l'estensione **Simple Math SDK** .  
  
    Vengono visualizzate informazioni aggiuntive sull'SDK. È possibile scegliere il collegamento **altre informazioni** da aprire https://docs.microsoft.com , come specificato nel file SDKManifest.xml in precedenza in questa procedura dettagliata.  
  
7. Nella finestra di dialogo **Gestione riferimenti** selezionare la casella di controllo **Simple Math SDK** , quindi scegliere il pulsante **OK** .  
  
8. Sulla barra dei menu scegliere **Visualizza**, **Visualizzatore oggetti**.  
  
9. Nell'elenco **Browse** scegliere **Simple Math**.  
  
     È ora possibile esplorare le funzionalità dell'SDK.  
  
10. In **Esplora soluzioni**aprire il file MainPage. XAML e sostituirne il contenuto con il codice XAML seguente:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Aggiornare MainPage.xaml.cs in modo che corrisponda al codice seguente:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Premere il tasto F5 per eseguire l'app.  
  
13. Nell'app immettere due numeri, scegliere un'operazione, quindi fare clic sul **=** pulsante.  
  
     Viene visualizzato il risultato corretto.  
  
    La creazione e l'uso di un SDK di estensione sono state completate.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: creazione di un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procedura dettagliata: creazione di un SDK tramite JavaScript](walkthrough-creating-an-sdk-using-javascript.md)   
 [Creazione di un Software Development Kit](../extensibility/creating-a-software-development-kit.md)
