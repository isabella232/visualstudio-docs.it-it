---
title: 'Procedura: Configurare Unit test destinati a una versione precedente di .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: adb6c011-5abd-41d2-8ead-08cd7579bf37
caps.latest.revision: 14
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 68a0c1b707011026d4fe58d86fc187b0152dae3e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795860"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Procedura: Configurare unit test destinati a una versione precedente di .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si crea un progetto di test in Microsoft Visual Studio, per impostazione predefinita viene impostata come destinazione la versione più recente di .NET Framework. Inoltre, se si esegue l'aggiornamento di progetti di test da versioni precedenti di Visual Studio, questi vengono aggiornati in modo da usare la versione più recente di .NET Framework come destinazione. Modificando le proprietà del progetto, è possibile ridefinire in modo esplicito la destinazione del progetto per le versioni precedenti di .NET Framework.  
  
 È possibile creare progetti di unit test destinati a specifiche versioni di .NET Framework. La versione di destinazione deve essere 3.5 o successiva e non può essere una versione client. Visual Studio consente il supporto di base seguente per gli unit test destinati a versioni specifiche:  
  
- È possibile creare progetti di unit test destinati a una specifica versione di .NET Framework.  
  
- È possibile eseguire unit test destinati a una versione specifica di .NET Framework da Visual Studio nel computer locale.  
  
- È possibile eseguire unit test destinati a una versione specifica di .NET Framework usando MSTest.exe dal prompt dei comandi.  
  
- È possibile eseguire unit test su un agente di compilazione come parte di una compilazione.  
  
  **Test delle applicazioni di SharePoint**  
  
  Le funzionalità elencate in precedenza consentono inoltre di scrivere unit test e test di integrazione per applicazioni di SharePoint tramite Visual Studio. [!INCLUDE[crabout](../includes/crabout-md.md)] come sviluppare applicazioni di SharePoint tramite Visual Studio, vedere [Creare soluzioni di SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631), [Compilazione e debug delle soluzioni SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) e [Verifica e debug del codice di SharePoint](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c).  
  
  **Limitazioni**  
  
  Quando si ridefinisce la destinazione dei progetti di test per l'uso di versioni precedenti di .NET Framework, si applicano le limitazioni seguenti:  
  
- In .NET Framework 3.5 è supportato il multitargeting per i progetti di test che contengono solo unit test. .NET Framework 3.5 non supporta altri tipi di test, ad esempio test di carico o test codificato dell'interfaccia utente. La modifica della destinazione è bloccata per i tipi di test diversi dagli unit test.  
  
- L'esecuzione di test che sono destinati a una versione precedente di .NET Framework è supportata solo nell'adattatore host predefinito. Non è supportata nell'adattatore host ASP.NET. Le applicazioni ASP.NET che devono essere eseguite nel contesto del server di sviluppo ASP.NET devono essere compatibili con la versione corrente di .NET Framework.  
  
- Il supporto per la raccolta dei dati è disabilitato quando si eseguono test che supportano il multitargeting di .NET Framework 3.5. È possibile eseguire il code coverage tramite gli strumenti da riga di comando di Visual Studio.  
  
- Non è possibile eseguire unit test che usano .NET Framework 3.5 in un computer remoto.  
  
- Non è possibile destinare unit test a versioni client precedenti del framework.  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Reindirizzamento di una versione specifica di .NET Framework per progetti unit test Visual Basic  
  
1.  Creare un nuovo progetto di unit test Visual Basic. Scegliere **Nuovo** dal menu **File** e quindi **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  In **Modelli installati** espandere **Visual Basic**. Selezionare **Test** e quindi selezionare il modello **Progetto di test**.  
  
3.  Nella casella di testo **Nome** digitare un nome per il progetto di test Visual Basic e scegliere **OK**.  
  
4.  In Esplora soluzioni scegliere **Proprietà** dal menu di scelta rapida del nuovo progetto di test Visual Basic.  
  
     Verranno visualizzate le proprietà del progetto di test Visual Basic.  
  
5.  Nella scheda **Compila** scegliere **Opzioni di compilazione avanzate**, come illustrato nella figura seguente.  
  
     ![Opzioni di compilazione avanzate](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")  
  
6.  Usare l'elenco a discesa **Framework di destinazione (tutte le configurazioni)** per impostare il framework di destinazione su **.NET Framework 3.5** o una versione successiva, come indicato nella didascalia B della figura seguente. Non specificare una versione client.  
  
     ![Elenco di riepilogo a discesa per il framework di destinazione](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Reindirizzamento di una versione specifica di .NET Framework per progetti unit test Visual C#  
  
1.  Creare un nuovo progetto di unit test Visual C#. Scegliere **Nuovo** dal menu **File** e quindi **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  In **Modelli installati** espandere **Visual C#**. Selezionare **Test** e quindi selezionare il modello **Progetto di test**.  
  
3.  Nella casella di testo **Nome** digitare un nome per il progetto di test Visual C# e scegliere **OK**.  
  
4.  In Esplora soluzioni scegliere **Proprietà** dal menu di scelta rapida del nuovo progetto di test Visual C#.  
  
     Verranno visualizzate le proprietà del progetto di test Visual C#.  
  
5.  Nella scheda **Applicazione** scegliere **Framework di destinazione** e quindi scegliere dall'elenco a discesa **.NET Framework 3.5** o una versione successiva per modificare il framework di destinazione, come indicato nella figura seguente. Non specificare una versione client.  
  
     ![Elenco di riepilogo a discesa per il framework di destinazione](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Reindirizzamento di una versione specifica di .NET Framework per progetti unit test C++/CLI  
  
1.  Creare un nuovo progetto di unit test Visual C++. Nel menu **File** fare clic su **Nuovo** e quindi su **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
    > [!WARNING]
    >  Per compilare unit test C++/CLI per una versione precedente di .NET Framework per Visual C++, è necessario usare la versione corrispondente di Visual Studio. Ad esempio, per impostare come destinazione .NET Framework 3.5, è necessario installare [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] e [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] Service Pack 1.  
  
2.  In **Modelli installati** espandere **Visual C++**. Selezionare **Test** e quindi selezionare il modello **Progetto di test**.  
  
3.  Nella casella di testo **Nome** digitare un nome per il progetto di test Visual C++ e scegliere **OK**.  
  
4.  In Esplora soluzioni scegliere **Scarica progetto** dal nuovo progetto di test Visual C++.  
  
5.  In Esplora soluzioni scegliere il progetto di test di Visual C++ scaricato, quindi selezionare **Modifica \<nome progetto>.vcxproj**.  
  
     Il file con estensione vcxproj verrà aperto nell'editor.  
  
6.  Impostare `TargetFrameworkVersion` sulla versione 3.5 o una versione successiva nel `PropertyGroup` con etichetta `"Globals"`. Non specificare una versione client:  
  
    ```  
    <PropertyGroup Label="Globals">  
        <TargetName>DefaultTest</TargetName>  
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>  
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>  
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>  
        <Keyword>ManagedCProj</Keyword>  
        <RootNamespace>CPP_Test</RootNamespace>  
      </PropertyGroup>  
  
    ```  
  
7.  Salvare e chiudere il file con estensione vcxproj.  
  
8.  In Esplora soluzioni selezionare **Ricarica progetto** dal menu di scelta rapida del nuovo progetto di test Visual C++.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione ed esecuzione di unit test per il codice esistente](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Creare soluzioni di SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Compilazione e debug delle soluzioni SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [Finestra di dialogo Impostazioni del compilatore avanzate (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
