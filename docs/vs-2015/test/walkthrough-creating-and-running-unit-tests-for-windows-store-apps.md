---
title: 'Procedura dettagliata: Creazione ed esecuzione di unit test per le applicazioni Windows Store | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5999edf14692e5ad51f56cb7989ea07eb0f11f5c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657117"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>Procedura dettagliata: creazione ed esecuzione di unit test per le applicazioni Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio sono inclusi il supporto per gli unit test di app di [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] gestite e i modelli della libreria di unit test per Visual C#, Visual Basic e Visual C++.

> [!TIP]
> Per altre informazioni sullo sviluppo di app di [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , vedere [Introduzione alle app di Windows Store](http://go.microsoft.com/fwlink/?LinkID=241410).

 In Visual Studio sono disponibili le funzionalità di testing unità seguenti:

- [Creare progetti di unit test](#CreateAndRunUnitTestWin8Tailored_Create)

- [Modificare il manifesto per il progetto di unit test](#CreateAndRunUnitTestWin8Tailored_Manifest)

- [Scrivere il codice dello unit test](#CreateAndRunUnitTestWin8Tailored_Code)

- [Eseguire unit test](#CreateAndRunUnitTestWin8Tailored_Run)

  Le procedure riportate di seguito descrivono i passaggi per creare, eseguire ed effettuare il debug di unit test per app di [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] gestite.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio

## <a name="CreateAndRunUnitTestWin8Tailored_Create"></a> Creare progetti di unit test

#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Per creare un progetto di unit test per un'app di Windows Store

1. Scegliere **Nuovo progetto** dal menu **File**.

     Verrà visualizzata la finestra di dialogo Nuovo progetto.

2. In Modelli, scegliere il linguaggio di programmazione con cui si desidera creare gli unit test, quindi scegliere la libreria di unit test per [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] associata. Ad esempio, scegliere **Visual C#** , quindi scegliere **Windows Store**e infine selezionare **Libreria unit test (applicazioni Windows Store)** .

    > [!NOTE]
    > In Visual Studio sono inclusi i modelli della libreria di unit test per Visual C#, Visual Basic e Visual C++.

3. (Facoltativo) Nella casella di testo **Nome** immettere il nome che si desidera usare per il progetto di unit test per [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)].

4. (Facoltativo) Modificare il percorso in cui si desidera creare il progetto immettendolo nella casella di testo **Percorso** oppure scegliendo il pulsante **Sfoglia** .

5. (Facoltativo) Nella casella di testo del nome **Soluzione** immettere il nome che si desidera usare per la soluzione.

6. Lasciare selezionata l'opzione **Crea directory per soluzione** e scegliere il pulsante **OK** .

     ![Libreria unit test personalizzata](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")

     Esplora soluzioni verrà popolato con il nuovo progetto di unit test per [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]e l'editor di codice visualizzerà lo unit test predefinito denominato UnitTest1.

     ![Nuovo progetto di unit test personalizzato](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> Modificare il manifesto per il progetto di unit test
 Può essere necessario modificare il manifesto per il progetto di unit test per fornire le funzionalità necessarie per eseguire l'app.

#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Per modificare il file manifesto dell'applicazione di Windows Store del progetto di unit test

1. In Esplora soluzioni, nel nuovo progetto di unit test per [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , fare clic con il pulsante destro del mouse sul file Package.appxmanifest e scegliere **Apri**.

     Verrà visualizzata la finestra Progettazione manifesto nella quale sarà possibile apportare le modifiche al manifesto.

2. In Progettazione manifesto scegliere la scheda **Funzionalità** .

3. Nell'elenco in **Funzionalità**selezionare le funzionalità necessarie per lo unit test e il codice per il test. Ad esempio, selezionare la casella di controllo **Internet** se lo unit test e il codice di cui si sta eseguendo il test necessitano della funzionalità di accesso a Internet.

    > [!NOTE]
    > Le funzionalità selezionate devono includere solo quelle necessarie affinché lo unit test per [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] funzioni correttamente. Non si devono mai includere funzionalità che non fanno parte dell'app di [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] sottoposta a test e in genere devono essere un sottoinsieme di funzionalità specificate per l'app di [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] sottoposta a test.

     Per altre informazioni su Progettazione manifesto, vedere [Configurare un pacchetto di app Windows 8.1 usando la finestra di progettazione del manifesto](https://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).

     ![Manifesto unit test](../test/media/unit-test-win8.png "Unit_Test_Win8_")

## <a name="CreateAndRunUnitTestWin8Tailored_Code"></a> Scrivere il codice dello unit test

#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Per scrivere il codice per lo unit test di un'app di Windows Store.

1. Nell'Editor di codice modificare lo unit test e aggiungere le asserzioni e la logica richieste per il test.

     Per altre informazioni, vedere [Utilizzo di classi Assert](http://go.microsoft.com/fwlink/?LinkID=224991) in MSDN Library.

## <a name="CreateAndRunUnitTestWin8Tailored_Run"></a> Eseguire unit test

#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Per compilare la soluzione ed eseguire lo unit test usando Esplora test

1. Dal menu **Test** scegliere **Finestre**, quindi scegliere **Esplora test**.

     Verrà visualizzato Esplora senza il test elencato.

2. Scegliere **Compila soluzione** dal menu **Compila**.

     Lo unit test viene elencato.

    > [!NOTE]
    > È necessario compilare la soluzione per aggiornare l'elenco degli unit test in Esplora test.

    > [!WARNING]
    > Problema noto di Visual Studio: è necessario aprire Esplora test prima di compilare il progetto di test.

3. In Esplora test, scegliere lo unit test creato.

    > [!TIP]
    > In Esplora test viene fornito un collegamento al codice sorgente accanto a **Origine:** .

4. Scegliere **Esegui tutto**.

     ![Esplora &#45; Unit Test eseguire unit test](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")

    > [!TIP]
    > È possibile selezionare uno o più unit test elencati in Esplora test, quindi fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati**.
    >
    >  Inoltre, è possibile scegliere di **eseguire il debug dei test selezionati**, di **aprire il test**e di usare l'opzione **Proprietà** .
    >
    >  ![Esplora &#45; unit test-menu di scelta rapida test UNI](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

     Lo unit test viene eseguito. Al termine, in Esplora test viene visualizzato lo stato del test, il tempo trascorso e viene fornito un collegamento all'origine.

     ![Test di Esplora &#45; unit test completato](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")

## <a name="external-resources"></a>Risorse esterne

### <a name="videos"></a>Video
 [Channel 9: Unit testing your Windows Store apps built using XAML (Testing unità delle app di Windows Store scritte in XAML)](http://go.microsoft.com/fwlink/?LinkId=226285)

### <a name="forums"></a>Forum
 [Visual Studio Unit Testing](http://go.microsoft.com/fwlink/?LinkId=224477) (Testing unità con Visual Studio)

### <a name="msdn-library"></a>MSDN Library
 [MSDN Library - Creazione ed esecuzione di unit test per il codice esistente (Visual Studio 2010)](http://go.microsoft.com/fwlink/?LinkID=223683)

## <a name="see-also"></a>Vedere anche
 [Test delle app dello Store con Visual Studio](../test/testing-store-apps-with-visual-studio.md) [compilare e testare un'app di Windows Store con Team Foundation Build](https://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)
