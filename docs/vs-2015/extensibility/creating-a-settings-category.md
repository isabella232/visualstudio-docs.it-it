---
title: Creazione di una categoria di impostazioni | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60b500fa0defff3fc038ae4550f580dd7742939d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885613"
---
# <a name="creating-a-settings-category"></a>Creazione di una categoria di impostazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata si crea una categoria di impostazioni di Visual Studio e lo usano per salvare i valori e ripristinare i valori da un file di impostazioni. Una categoria di impostazioni è un gruppo di proprietà correlate che vengono visualizzati come un "punto di impostazioni personalizzate"; vale a dire come una casella di controllo nel **Importa / Esporta impostazioni** procedura guidata. (È possibile trovarlo nel **strumenti** menu.) Le impostazioni vengono salvate o ripristinate come una categoria e le singole impostazioni non vengono visualizzate nella procedura guidata. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si crea una categoria di impostazioni mediante la derivazione da di <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.  
  
 Per avviare questa procedura dettagliata, è necessario completare prima la prima sezione del [creazione di una pagina di opzioni](../extensibility/creating-an-options-page.md). La griglia delle proprietà opzioni risulta consente di esaminare e modificare le proprietà nella categoria. Dopo aver salvato la categoria della proprietà in un file di impostazioni, si esamina il file per vedere come vengono archiviati i valori delle proprietà.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Creazione di una categoria di impostazioni  
 In questa sezione si usa un punto di impostazioni personalizzate per salvare e ripristinare i valori di categoria di impostazioni.  
  
#### <a name="to-create-a-settings-category"></a>Per creare una categoria di impostazioni  
  
1.  Completare la [creazione di una pagina di opzioni](../extensibility/creating-an-options-page.md).  
  
2.  Aprire il file VSPackage.resx e aggiungere le risorse di queste tre stringhe:  
  
    |nome|Valore|  
    |----------|-----------|  
    |106|La categoria|  
    |107|Impostazioni personali|  
    |108|OptionInteger e OptionFloat|  
  
     Ciò consente di creare le risorse di tale nome la categoria "My Category", l'oggetto "My Settings" e la descrizione della categoria "OptionInteger e OptionFloat".  
  
    > [!NOTE]
    >  Di questi tre, solo il nome della categoria non vengono visualizzate nella procedura guidata Importa / Esporta impostazioni.  
  
3.  In MyToolsOptionsPackage.cs, aggiungere un `float` proprietà denominata `OptionFloat` per il `OptionPageGrid` classe, come illustrato nell'esempio seguente.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Il `OptionPageGrid` categoria denominata "My Category" ora è costituita da due proprietà, `OptionInteger` e `OptionFloat`.  
  
4.  Aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> per il `MyToolsOptionsPackage` classe e assegnargli CategoryName "My Category", assegnargli ObjectName "My Settings" e impostare isToolsOptionPage su true. Impostare il categoryResourceID, objectNameResourceID e DescriptionResourceID alla risorsa di stringa corrispondente che ID creato in precedenza.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Compilare il progetto e avviare il debug. Nell'istanza sperimentale dovrebbe che **pagina della griglia My** ha ora i valori sia integer e float.  
  
## <a name="examining-the-settings-file"></a>Esaminare il File di impostazioni  
 In questa sezione vengono esportati valori di categoria di proprietà in un file di impostazioni. Si esamina il file e quindi importare i valori nella categoria della proprietà.  
  
1.  Avviare il progetto in modalità di debug premendo F5. Verrà avviata l'istanza sperimentale.  
  
2.  Aprire il **Strumenti / opzioni** finestra di dialogo.  
  
3.  Nella visualizzazione albero nel riquadro sinistro, espandere **My Category** e quindi fare clic su **My pagina della griglia**.  
  
4.  Modificare il valore della **OptionFloat** a 3,1416 e **OptionInteger** a 12. Fare clic su **OK**.  
  
5.  Nel **degli strumenti** menu, fare clic su **Importa / Esporta impostazioni**.  
  
     Il **Importa / Esporta impostazioni** procedura guidata viene visualizzata.  
  
6.  Assicurarsi che **Esporta le impostazioni di ambiente selezionate** sia selezionata e quindi fare clic su **successivo**.  
  
     Il **scegliere le impostazioni da esportare** verrà visualizzata la pagina.  
  
7.  Fare clic su **impostazioni personali**.  
  
     Il **Description** diventa **OptionInteger e OptionFloat**.  
  
8.  Verificare che l'opzione **My Settings** è l'unica categoria che sia selezionata e quindi fare clic su **successivo**.  
  
     Il **nome del File di impostazioni** verrà visualizzata la pagina.  
  
9. Denominare il nuovo file di impostazioni `MySettings.vssettings` e salvarlo in una directory appropriata. Scegliere **Fine**.  
  
     Il **esportazione completa** pagina indica che le impostazioni sono state esportate correttamente.  
  
10. Nel **File** dal menu **Open**, quindi fare clic su **File**. Individuare `MySettings.vssettings` e aprirlo.  
  
     È possibile trovare la categoria della proprietà che è stata esportata nella sezione seguente del file (i GUID saranno diverso).  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     Si noti che il nome di categoria full è formato mediante l'aggiunta di un carattere di sottolineatura per il nome categoria seguito dal nome dell'oggetto. OptionFloat e OptionInteger vengono visualizzati nella categoria, insieme ai relativi valori esportati.  
  
11. Chiudere il file di impostazioni senza modificarlo.  
  
12. Nel **degli strumenti** dal menu fare clic su **opzioni**, espandere **My Category**, fare clic su **My pagina della griglia** e quindi modificare il valore di  **OptionFloat** da 1.0 e **OptionInteger** su 1. Fare clic su **OK**.  
  
13. Nel **degli strumenti** menu, fare clic su **Importa / Esporta impostazioni**, selezionare **Importa le impostazioni di ambiente selezionate**e quindi fare clic su **successivo**.  
  
     Il **salvare le impostazioni correnti** verrà visualizzata la pagina.  
  
14. Selezionare **No, importa soltanto le nuove impostazioni** e quindi fare clic su **successivo**.  
  
     Il **sceglie una raccolta di impostazioni da importare** verrà visualizzata la pagina.  
  
15. Selezionare il `MySettings.vssettings` del file nei **My Settings** nodo della visualizzazione albero. Se il file non viene visualizzato nella visualizzazione albero, fare clic su **esplorare** e trovarla. Scegliere **Avanti**.  
  
     Il **scegliere le impostazioni da importare** verrà visualizzata la finestra di dialogo.  
  
16. Verificare che l'opzione **My Settings** sia selezionata e quindi fare clic su **fine**. Quando la **importazione completa** verrà visualizzata la pagina, fare clic su **Chiudi**.  
  
17. Nel **degli strumenti** dal menu fare clic su **opzioni**, espandere **My Category**, fare clic su **My pagina della griglia** e verificare che i valori di categoria di proprietà stato ripristinato.

