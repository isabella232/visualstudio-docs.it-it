---
title: Creazione di una categoria di impostazioni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739614"
---
# <a name="create-a-settings-category"></a>Creare una categoria di impostazioni

In questa procedura dettagliata si crea una categoria di impostazioni di Visual Studio e la si usa per salvare i valori e ripristinarli da un file di impostazioni. Una categoria di impostazioni è un gruppo di proprietà correlate che vengono visualizzate come un "punto di impostazioni personalizzate"; ovvero come casella di controllo **nell'Importazione/Esportazione** guidata Impostazioni. (È possibile trovarlo nel menu **Strumenti.)** Le impostazioni vengono salvate o ripristinate come categoria e le singole impostazioni non vengono visualizzate nella procedura guidata. Per altre informazioni, vedere [Impostazioni dell'ambiente](../ide/environment-settings.md).

È possibile creare una categoria di <xref:Microsoft.VisualStudio.Shell.DialogPage> impostazioni derivandola dalla classe.

Per iniziare questa procedura dettagliata, è innanzitutto necessario completare la prima sezione della [pagina Crea una pagina Opzioni.](../extensibility/creating-an-options-page.md) La griglia delle proprietà Opzioni risultante consente di esaminare e modificare le proprietà nella categoria. Dopo aver salvato la categoria di proprietà in un file di impostazioni, esaminare il file per vedere come vengono archiviati i valori delle proprietà.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-settings-category"></a>Creare una categoria di impostazioni
 In questa sezione viene utilizzato un punto di impostazioni personalizzato per salvare e ripristinare i valori della categoria di impostazioni.

### <a name="to-create-a-settings-category"></a>Per creare una categoria di impostazioni

1. Completare la [pagina Crea un'opzione](../extensibility/creating-an-options-page.md).

2. Aprire il file VSPackage.resx e aggiungere queste tre risorse stringa:Open the *VSPackage.resx* file and add these three string resources:

    |Nome|valore|
    |----------|-----------|
    |106|La mia categoria|
    |107|Impostazioni personali|
    |108|OptionInteger e OptionFloat|

     In questo modo vengono create risorse che assegnano al nome della categoria "My Category", dell'oggetto "My Settings" e della descrizione della categoria "OptionInteger and OptionFloat".

    > [!NOTE]
    > Di questi tre, solo il nome della categoria non viene visualizzato **nell'Importazione/Esportazione** guidata Impostazioni.

3. In *MyToolsOptionsPackage.cs*, `float` aggiungere `OptionFloat` una `OptionPageGrid` proprietà denominata alla classe , come illustrato nell'esempio seguente.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > La `OptionPageGrid` categoria denominata "My Category" è `OptionInteger` `OptionFloat`ora costituita dalle due proprietà e .

4. Aggiungere <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a `MyToolsOptionsPackage` alla classe e assegnarle il CategoryName "My Category", assegnargli il NomeOggetto "My Settings" e impostare isToolsOptionPage su true. Impostare categoryResourceID, objectNameResourceID e DescriptionResourceID per gli ID di risorsa stringa corrispondenti creati in precedenza.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Compilare il progetto e avviare il debug. Nell'istanza sperimentale si dovrebbe vedere che **My Grid Page** ora ha valori interi e float.

## <a name="examine-the-settings-file"></a>Esaminare il file di impostazioni
 In questa sezione vengono esportati i valori delle categorie di proprietà in un file di impostazioni. Esaminare il file e quindi importare nuovamente i valori nella categoria di proprietà.

1. Avviare il progetto in modalità di debug premendo **F5**. In questo modo viene avviata l'istanza sperimentale.

2. Aprire la finestra di dialogo**Opzioni** **degli strumenti.** > 

3. Nel riquadro sinistro della visualizzazione struttura espandere **Categoria personale** e quindi fare clic su **Pagina griglia**personale .

4. Modificare il valore di **OptionFloat** in 3.1416 e **OptionInteger** in 12. Fare clic su **OK**.

5. Scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**.

     Viene visualizzata la procedura guidata **Importa/Esporta impostazioni.**

6. Assicurarsi che **l'opzione Esporta impostazioni di ambiente selezionate** sia selezionata e quindi fare clic su **Avanti**.

     Viene visualizzata la pagina **Scegliere le impostazioni da esportare.**

7. Fare clic su **Impostazioni personali**.

     La **descrizione** viene modificata in **OptionInteger e OptionFloat**.

8. Assicurarsi che **Impostazioni personali** sia l'unica categoria selezionata e quindi fare clic su **Avanti**.

     Viene visualizzata la pagina **Assegna un nome al file di impostazioni.**

9. Assegnare al nuovo file di impostazioni il nome *MySettings.vssettings* e salvarlo in una directory appropriata. Fare clic su **Fine**.

     La pagina **Esporta completata** segnala che le impostazioni sono state esportate correttamente.

10. Scegliere **Apri** dal menu **File**e quindi fare clic su **File**. Individuare *MySettings.vssettings* e aprirlo.

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

     Si noti che il nome completo della categoria è formato dall'aggiunta di un segno di sottolineatura al nome della categoria seguito dal nome dell'oggetto. OptionFloat e OptionInteger vengono visualizzati nella categoria, insieme ai relativi valori esportati.

11. Chiudere il file di impostazioni senza modificarlo.

12. Scegliere **Opzioni**dal menu **Strumenti** , espandere **Categoria personale**, Pagina **griglia** personale e quindi impostare il valore di **OptionFloat** su 1.0 e **OptionInteger** su 1. Fare clic su **OK**.

13. Scegliere **Importa/Esporta impostazioni**dal menu **Strumenti** , selezionare **Importa impostazioni di ambiente selezionate**e quindi fare clic su **Avanti**.

     Viene visualizzata la pagina **Salva impostazioni correnti.**

14. Selezionare **No, importa solo le nuove impostazioni** e quindi fare clic su **Avanti**.

     Viene visualizzata la pagina **Scegliere una raccolta di impostazioni da importare.**

15. Selezionare il file *MySettings.vssettings* nel nodo **Impostazioni personali** della visualizzazione struttura. Se il file non viene visualizzato nella vista ad albero, fare clic su **Sfoglia** e individuarlo. Fare clic su **Avanti**.

     Viene visualizzata la finestra di dialogo **Scegli impostazioni da importare.**

16. Assicurarsi che **My Settings** sia selezionato e quindi fare clic su **Fine**. Quando viene visualizzata la pagina **Importazione completata,** fare clic su **Chiudi**.

17. Scegliere **Opzioni**dal menu **Strumenti** , espandere **Categoria personale**, fare clic su Pagina **griglia** personale e verificare che i valori della categoria di proprietà siano stati ripristinati.
