---
title: Creazione di una categoria di impostazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d50ca998efa034b1d4392c1fb7cecb8de8ed06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904024"
---
# <a name="create-a-settings-category"></a>Crea una categoria di impostazioni

In questa procedura dettagliata viene creata una categoria di impostazioni di Visual Studio che viene utilizzata per salvare i valori e ripristinare i valori da un file di impostazioni. Una categoria di impostazioni è un gruppo di proprietà correlate che vengono visualizzate come un "punto di impostazioni personalizzato"; ovvero come una casella di controllo nella procedura guidata **Importa/Esporta impostazioni** . (È possibile trovarlo nel menu **strumenti** ). Le impostazioni vengono salvate o ripristinate come una categoria e le singole impostazioni non vengono visualizzate nella procedura guidata. Per altre informazioni, vedere [Impostazioni dell'ambiente](../ide/environment-settings.md).

Per creare una categoria di impostazioni, derivarla dalla <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.

Per iniziare questa procedura dettagliata, è necessario completare prima la prima sezione di [creare una pagina di opzioni](../extensibility/creating-an-options-page.md). La griglia delle proprietà Opzioni risultanti consente di esaminare e modificare le proprietà nella categoria. Dopo aver salvato la categoria di proprietà in un file di impostazioni, esaminare il file per vedere come vengono archiviati i valori delle proprietà.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Crea una categoria di impostazioni
 In questa sezione viene usato un punto di impostazioni personalizzato per salvare e ripristinare i valori della categoria impostazioni.

### <a name="to-create-a-settings-category"></a>Per creare una categoria di impostazioni

1. Completare la [pagina creare una pagina di opzioni](../extensibility/creating-an-options-page.md).

2. Aprire il file *VSPackage. resx* e aggiungere le tre risorse stringa seguenti:

    |Nome|Valore|
    |----------|-----------|
    |106|Categoria personale|
    |107|Impostazioni personali|
    |108|OptionInteger e OptionFloat|

     Vengono create risorse che denominano la categoria "My Category", l'oggetto "My Settings" e la descrizione della categoria "OptionInteger and OptionFloat".

    > [!NOTE]
    > Di questi tre, solo il nome della categoria non viene visualizzato nell' **importazione/esportazione guidata delle impostazioni** .

3. In *MyToolsOptionsPackage.cs*aggiungere una `float` proprietà denominata `OptionFloat` alla `OptionPageGrid` classe, come illustrato nell'esempio seguente.

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
    > La `OptionPageGrid` categoria denominata "My Category" è ora costituita dalle due proprietà, `OptionInteger` e `OptionFloat` .

4. Aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> alla `MyToolsOptionsPackage` classe e assegnargli il valore CategoryName "My Category", assegnare a esso il nomeoggetto "My Settings" e impostare isToolsOptionPage su true. Impostare categoryResourceID, objectNameResourceID e DescriptionResourceID sugli ID di risorsa di stringa corrispondenti creati in precedenza.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Compilare il progetto e avviare il debug. Nell'istanza sperimentale si noterà che **la pagina della griglia** dispone ora di valori integer e float.

## <a name="examine-the-settings-file"></a>Esaminare il file di impostazioni
 In questa sezione si esportano i valori delle categorie di proprietà in un file di impostazioni. Esaminare il file e quindi importare di nuovo i valori nella categoria della proprietà.

1. Avviare il progetto in modalità di debug premendo **F5**. Viene avviata l'istanza sperimentale.

2. Aprire la **Tools**  >  finestra di dialogo**Opzioni** strumenti.

3. Nella visualizzazione albero nel riquadro sinistro espandere la **categoria** e quindi fare clic sulla **pagina della griglia**.

4. Modificare il valore di **optionFloat** in 3,1416 e **OptionInteger** su 12. Fare clic su **OK**.

5. Scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**.

     Verrà visualizzata l' **importazione/esportazione guidata delle impostazioni** .

6. Verificare che l'opzione **Esporta impostazioni di ambiente selezionate** sia selezionata, quindi fare clic su **Avanti**.

     Verrà visualizzata la pagina **scegliere le impostazioni da esportare** .

7. Fare clic su **impostazioni personali**.

     La **Descrizione** viene modificata in **OptionInteger e optionFloat**.

8. Assicurarsi che **My Settings** sia l'unica categoria selezionata, quindi fare clic su **Avanti**.

     Viene visualizzata la pagina **nome del file di impostazioni** .

9. Assegnare al nuovo file di impostazioni il nome Settings *. vssettings* e salvarlo in una directory appropriata. Fare clic su **Fine**.

     Nella pagina **esportazione completata** viene segnalato che le impostazioni sono state esportate correttamente.

10. Scegliere **Apri** dal menu **File**e quindi fare clic su **File**. Individuare *impostazioni. vssettings* e aprirlo.

     È possibile trovare la categoria di proprietà esportata nella sezione seguente del file (i GUID sono diversi).

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

12. Scegliere **Opzioni**dal menu **strumenti** , espandere **categoria**, fare clic sulla **pagina della griglia** e quindi modificare il valore di **optionFloat** su 1,0 e **OptionInteger** su 1. Fare clic su **OK**.

13. Nel menu **strumenti** fare clic su **Importa/Esporta impostazioni**, selezionare **Importa le impostazioni di ambiente selezionate**, quindi fare clic su **Avanti**.

     Viene visualizzata la pagina **Salva impostazioni correnti** .

14. Selezionare **No, importa solo nuove impostazioni** e quindi fare clic su **Avanti**.

     Viene visualizzata la pagina **scegliere una raccolta di impostazioni da importare** .

15. Selezionare il file *Settings. vssettings* nel nodo **impostazioni personali** della visualizzazione albero. Se il file non viene visualizzato nella visualizzazione albero, fare clic su **Sfoglia** e trovarlo. Fare clic su **Avanti**.

     Verrà visualizzata la finestra **di dialogo scegliere le impostazioni da importare** .

16. Assicurarsi che sia selezionata l'opzione **impostazioni personali** , quindi fare clic su **fine**. Quando viene visualizzata la pagina **importazione completata** , fare clic su **Chiudi**.

17. Scegliere **Opzioni**dal menu **strumenti** , espandere **categoria**, fare clic sulla **pagina della griglia** e verificare che i valori della categoria di proprietà siano stati ripristinati.
