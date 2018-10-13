---
title: 'Procedura dettagliata: Creazione di un SDK tramite c# o Visual Basic | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96b4ded80d3c00c0f2c7a5c9037758f72907ea28
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215605"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Procedura dettagliata: creazione di un SDK con C# o Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata si apprenderà come creare un SDK della libreria matematica semplice con Visual c# e quindi creare il pacchetto SDK come un Visual Studio Extension (VSIX). È possibile completare le procedure seguenti:  
  
-   [Per creare il componente SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Per creare il progetto di estensione SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Per creare un'app di esempio che usa la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Per creare il componente SimpleMath Windows Runtime  
  
1.  Nella barra dei menu, scegliere **File**, **New**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual c#** o **Visual Basic**, scegliere il **Windows Store** nodo, quindi scegliere il **componente di Runtime di Windows** modello.  
  
3.  Nel **nome** , specificare **SimpleMath**, quindi scegliere il **OK** pulsante.  
  
4.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMath** nodo del progetto e quindi scegliere **proprietà**.  
  
5.  Rinominare **Class1.cs** al **Arithmetic.cs** e aggiornarlo in modo che corrisponda al codice seguente:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6.  Nella **Esplora soluzioni**, aprire il menu di scelta rapida per il **soluzione 'SimpleMath'** nodo, quindi scegliere **Configuration Manager**.  
  
     Il **Configuration Manager** verrà visualizzata la finestra di dialogo.  
  
7.  Nel **configurazione soluzione attiva** casella di riepilogo **rilascio**.  
  
8.  Nel **Configuration** colonna, verificare che **SimpleMath** riga è impostata su **rilascio**e quindi scegliere il **Chiudi** pulsante per accettare il modificare.  
  
    > [!IMPORTANT]
    >  il SDK per il componente SimpleMath include solo una configurazione. Questa configurazione deve essere la build di versione o le app che usano il componente non passare la certificazione il[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMath** nodo del progetto e quindi scegliere **compilare**.  
  
##  <a name="createVSIX"></a> Per creare il progetto di estensione SimpleMathVSIX  
  
1.  Nel menu di scelta rapida per il **soluzione 'SimpleMath'** nodo, scegliere **Add**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual c#** o **Visual Basic**, scegliere il **estendibilità** nodo, quindi scegliere il **progetto VSIX** modello.  
  
3.  Nel **nome** , specificare **SimpleMathVSIX**, quindi scegliere il **OK** pulsante.  
  
4.  Nelle **Esplora soluzioni**, scegliere il **vsixmanifest** elemento.  
  
5.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
6.  Sostituire il codice XML esistente con il codice XML seguente:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  Nelle **Esplora soluzioni**, scegliere il **SimpleMathVSIX** progetto.  
  
8.  Nella barra dei menu, scegliere **Project**, **Aggiungi nuovo elemento**.  
  
9. Nell'elenco degli **gli elementi comuni**, espandere **dati**, quindi scegliere **File XML**.  
  
10. Nel **nome** , specificare `SDKManifest.xml`, quindi scegliere il **Aggiungi** pulsante.  
  
11. In **Esplora soluzioni**, aprire il menu di scelta rapida `SDKManifest.xml`, scegliere **le proprietà**e quindi modificare il valore della **Includi in VSIX** proprietà per **True**.  
  
12. Sostituisci il contenuto del file con il codice XML riportato di seguito:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. Nel **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMathVSIX** del progetto, scegliere **Add**, quindi scegliere **nuova cartella**.  
  
14. Rinominare la cartella per `references`.  
  
15. Aprire il menu di scelta rapida per il **riferimenti** cartella, scegliere **Add**, quindi scegliere **nuova cartella**.  
  
16. Rinominare la sottocartella `commonconfiguration`, creare una sottocartella all'interno di esso e assegnare un nome della sottocartella `neutral`.  
  
17. Ripetere i quattro passaggi precedenti, questa volta rinominato la cartella prima di `redist`.  
  
     Il progetto contiene ora la struttura di cartelle seguente:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMath** del progetto e quindi scegliere **Apri cartella in Esplora File**.  
  
19. Nelle **Esplora File**, passare alla cartella bin\Release, aprire il menu di scelta rapida per il file SimpleMath.winmd e quindi scegliere **copia**.  
  
20. Nelle **Esplora soluzioni**, incollare il file nella cartella references\commonconfiguration\neutral il **SimpleMathVSIX** progetto.  
  
21. Ripetere il passaggio precedente, incollare il file SimpleMath.pri nella cartella redist\commonconfiguration\neutral il **SimpleMathVSIX** progetto.  
  
22. Nelle **Esplora soluzioni**, scegliere **SimpleMath.winmd**.  
  
23. Nella barra dei menu, scegliere **View**, **proprietà** (tastiera: premere il tasto F4).  
  
24. Nel **delle proprietà** finestra Modifica il **azione di compilazione** proprietà **contenuto**e quindi modificare il **Includi in VSIX** proprietà  **True**.  
  
25. Nelle **Esplora soluzioni**, ripetere questo processo per **SimpleMath.pri**.  
  
26. Nelle **Esplora soluzioni**, scegliere il **SimpleMathVSIX** progetto.  
  
27. Nella barra dei menu, scegliere **compilare**, **compilazione SimpleMathVSIX**.  
  
28. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **SimpleMathVSIX** del progetto e quindi scegliere **Apri cartella in Esplora File**.  
  
29. Nelle **Esplora File**, passare alla cartella \bin\Release, e quindi eseguire SimpleMathVSIX.vsix per installarlo.  
  
30. Scegliere il **installare** pulsante, attendere il completamento dell'installazione e quindi riavviare Visual Studio.  
  
##  <a name="createSample"></a> Per creare un'app di esempio che usa la libreria di classi  
  
1.  Nella barra dei menu, scegliere **File**, **New**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli, espandere **Visual c#** oppure **Visual Basic**, quindi scegliere il **Windows Store** nodo.  
  
3.  Scegliere il **App vuota** modello, nome del progetto **ArithmeticUI**, quindi scegliere il **OK** pulsante.  
  
4.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **ArithmeticUI** del progetto e quindi scegliere **Add**, **riferimento**.  
  
5.  Nell'elenco dei tipi di riferimento, espandere **Windows**, quindi scegliere **estensioni**.  
  
6.  Nel riquadro dei dettagli, scegliere il **semplice Math SDK** estensione.  
  
     Vengono visualizzate informazioni aggiuntive sul SDK. È possibile scegliere il **per altre informazioni** collegamento per aprire http://www.msdn.microsoft.com, come specificato nel file Sdkmanifest più indietro in questa procedura dettagliata.  
  
7.  Nel **gestione riferimenti** finestra di dialogo, seleziona la **SDK matematiche semplici** casella di controllo e quindi scegliere il **OK** pulsante.  
  
8.  Nella barra dei menu, scegliere **View**, **Visualizzatore oggetti**.  
  
9. Nel **esplorare** elenco, scegliere **semplice operazione matematica**.  
  
     È ora possibile esplorare What ' s nel SDK.  
  
10. Nelle **Esplora soluzioni**, aprire MainPage. XAML e sostituirne il contenuto con il seguente XAML:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. MainPage.xaml.cs aggiornare in modo che corrisponda il codice seguente:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Premere il tasto F5 per eseguire l'app.  
  
13. Nell'app, immettere tutti i due numeri, scegliere un'operazione e quindi scegliere il **=** pulsante.  
  
     Viene visualizzato il risultato corretto.  
  
 Avere creato e usato un SDK di estensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procedura dettagliata: Creazione di un SDK con JavaScript](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Creazione di un Software Development Kit](../extensibility/creating-a-software-development-kit.md)

