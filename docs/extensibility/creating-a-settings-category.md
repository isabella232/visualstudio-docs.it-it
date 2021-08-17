---
title: Creazione di un Impostazioni di | Microsoft Docs
description: Informazioni su come creare una Visual Studio delle impostazioni e usarla per salvare e ripristinare i valori da un file di impostazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: bbdc247e11930f05649b8e7b3c9d6d4cb1740aab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043713"
---
# <a name="create-a-settings-category"></a>Creare una categoria di impostazioni

In questa procedura dettagliata viene creata una Visual Studio delle impostazioni e viene utilizzata per salvare i valori in e ripristinare i valori da un file di impostazioni. Una categoria di impostazioni è un gruppo di proprietà correlate che vengono visualizzate come "punto di impostazioni personalizzate". ad esempio come casella di controllo nella procedura guidata Importa ed **esporta Impostazioni** guidata. È possibile trovarlo **nel** menu Strumenti. Impostazioni vengono salvate o ripristinate come categoria e le singole impostazioni non vengono visualizzate nella procedura guidata. Per altre informazioni, vedere [Impostazioni dell'ambiente](../ide/environment-settings.md).

Per creare una categoria di impostazioni, derivarla dalla <xref:Microsoft.VisualStudio.Shell.DialogPage> classe .

Per avviare questa procedura dettagliata, è prima necessario completare la prima sezione [della pagina Crea un'opzione](../extensibility/creating-an-options-page.md). La griglia delle proprietà Opzioni risultante consente di esaminare e modificare le proprietà nella categoria. Dopo aver salvato la categoria di proprietà in un file di impostazioni, esaminare il file per vedere come vengono archiviati i valori delle proprietà.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-settings-category"></a>Creare una categoria di impostazioni
 In questa sezione si usa un punto di impostazioni personalizzato per salvare e ripristinare i valori della categoria di impostazioni.

### <a name="to-create-a-settings-category"></a>Per creare una categoria di impostazioni

1. Completare [la pagina Crea un'opzione](../extensibility/creating-an-options-page.md).

2. Aprire il file *VSPackage.resx* e aggiungere queste tre risorse stringa:

    |Nome|Valore|
    |----------|-----------|
    |106|Categoria|
    |107|Impostazioni personali|
    |108|OptionInteger e OptionFloat|

     In questo modo vengono create risorse con il nome "My Category", l'oggetto "My Impostazioni" e la descrizione della categoria "OptionInteger e OptionFloat".

    > [!NOTE]
    > Di questi tre, solo il nome della categoria non viene visualizzato nella procedura guidata **Importa ed esporta Impostazioni** guidata.

3. In *MyToolsOptionsPackage.cs* aggiungere una `float` proprietà denominata alla classe , come illustrato `OptionFloat` `OptionPageGrid` nell'esempio seguente.

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
    > La `OptionPageGrid` categoria denominata "My Category" è ora costituita dalle due proprietà `OptionInteger` e `OptionFloat` .

4. Aggiungere un oggetto alla classe e assegnargli <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `MyToolsOptionsPackage` categoryName "My Category", assegnargli ObjectName "My Impostazioni" e impostare isToolsOptionPage su true. Impostare categoryResourceID, objectNameResourceID e DescriptionResourceID sull'ID risorsa stringa corrispondente creato in precedenza.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Compilare il progetto e avviare il debug. Nell'istanza sperimentale si dovrebbe vedere che **My Grid Page** ha ora valori integer e float.

## <a name="examine-the-settings-file"></a>Esaminare il file di impostazioni
 In questa sezione i valori delle categorie di proprietà vengono esportati in un file di impostazioni. Esaminare il file e quindi importare nuovamente i valori nella categoria di proprietà.

1. Avviare il progetto in modalità di debug premendo **F5.** Verrà avviata l'istanza sperimentale.

2. Aprire la **finestra di dialogo**  >  **Opzioni** degli strumenti.

3. Nella visualizzazione albero nel riquadro sinistro espandere **Categoria** e quindi fare clic su **Pagina griglia.**

4. Impostare il valore di **OptionFloat** su 3,1416 e **OptionInteger** su 12. Fare clic su **OK**.

5. Scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**.

     Verrà **visualizzata la procedura guidata Importa Impostazioni** esporta.

6. Assicurarsi che **l'opzione Esporta le impostazioni di ambiente** selezionate sia selezionata e quindi fare clic su **Avanti.**

     Verrà **visualizzata la Impostazioni scegliere l'esportazione.**

7. Fare **clic su My Impostazioni**.

     La **descrizione** cambia **in OptionInteger e OptionFloat**.

8. Assicurarsi che **My Impostazioni** sia l'unica categoria selezionata e quindi fare clic su **Avanti.**

     Verrà **visualizzata la pagina Impostazioni File** di configurazione.

9. Assegnare al nuovo file *di impostazioni il nome MySettings.vssettings* e salvarlo in una directory appropriata. Fare clic su **Fine**.

   Il `.vssettings` file è il Visual Studio delle impostazioni. Lo schema del file è aperto. In genere, lo schema segue una struttura XML in cui ogni categoria è un tag, che a sua volta può contenere tag di sottocategoria. Questi tag di sottocatego; possono contenere tag di valori di proprietà. Anche se la maggior parte dei pacchetti usa la struttura comune, qualsiasi pacchetto Visual Studio può fornire codice XML arbitrario al file con lo schema scelto.

   La **pagina Esportazione completata** segnala che le impostazioni sono state esportate correttamente.

10. Scegliere **Apri** dal menu **File** e quindi fare clic su **File**. Individuare *MySettings.vssettings* e aprirlo.

     È possibile trovare la categoria di proprietà esportata nella sezione seguente del file (i GUID saranno diversi).

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

     Si noti che il nome completo della categoria è formato dall'aggiunta di un carattere di sottolineatura al nome della categoria seguito dal nome dell'oggetto. OptionFloat e OptionInteger vengono visualizzati nella categoria, insieme ai relativi valori esportati.

11. Chiudere il file di impostazioni senza modificarlo.

12. Scegliere Opzioni **dal** menu Strumenti **,** espandere  **Categoria,** fare clic su Pagina griglia e quindi impostare il valore di **OptionFloat** su 1.0 e **OptionInteger** su 1. Fare clic su **OK**.

13. Scegliere **Importa ed** esporta dal menu **Strumenti** Impostazioni, selezionare Importa impostazioni **di ambiente selezionate** e quindi fare clic su **Avanti.**

     Verrà **visualizzata la pagina Salva Impostazioni** corrente.

14. Selezionare **No, importare solo nuove impostazioni e** quindi fare clic su **Avanti.**

     Verrà **visualizzata la pagina Scegliere una Impostazioni da** importare.

15. Selezionare il file *MySettings.vssettings* nel nodo **My Impostazioni** della visualizzazione albero. Se il file non viene visualizzato nella visualizzazione albero, fare clic **su Sfoglia** e trovarlo. Fare clic su **Avanti**.

     Verrà **visualizzata la Impostazioni finestra di dialogo** Scegli Impostazioni importa.

16. Assicurarsi che **l'opzione Impostazioni** sia selezionata e quindi fare clic su **Fine**. Quando viene **visualizzata la pagina** Importazione completata, fare clic su **Chiudi**.

17. Scegliere **Opzioni** dal menu Strumenti **,** espandere **Categoria,** fare clic su **Pagina** griglia e verificare che i valori delle categorie di proprietà siano stati ripristinati.
