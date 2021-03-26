---
title: 'Procedura dettagliata: salvataggio delle impostazioni utente in una pagina iniziale | Microsoft Docs'
description: Informazioni su come salvare in modo permanente le impostazioni utente per la pagina iniziale salvando un'impostazione nel registro di sistema utilizzando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: be270fe8b76b6cd07bd27350eabceb5eecbc446b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078331"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Procedura dettagliata: salvare le impostazioni utente in una pagina iniziale

È possibile salvare in permanente le impostazioni utente per la pagina iniziale. Seguendo questa procedura dettagliata, è possibile creare un controllo che salva un'impostazione nel registro di sistema quando l'utente fa clic su un pulsante e quindi recupera l'impostazione ogni volta che viene caricata la pagina iniziale. Poiché il modello di progetto di pagina iniziale include un controllo utente personalizzabile e il codice XAML predefinito della pagina iniziale chiama tale controllo, non è necessario modificare la pagina iniziale.

L'archivio impostazioni di cui viene creata un'istanza in questa procedura dettagliata è un'istanza dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interfaccia, che legge e scrive nel seguente percorso del registro di sistema quando viene chiamato: **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName>**

Quando è in esecuzione nell'istanza sperimentale di Visual Studio, l'archivio delle impostazioni legge e scrive in **HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName> .**

Per ulteriori informazioni su come salvare in modo permanente le impostazioni, vedere [estensione delle impostazioni utente e delle opzioni](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> È possibile scaricare il modello di progetto di pagina iniziale usando **Gestione estensioni**.

## <a name="set-up-the-project"></a>Configurare il progetto

1. Creare un progetto di pagina iniziale come descritto in [creare una pagina iniziale personalizzata](creating-a-custom-start-page.md). Denominare il progetto **SaveMySettings**.

2. In **Esplora soluzioni** aggiungere i riferimenti ad assembly seguenti al progetto StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. Shell. Interop. 11.0

3. Aprire il *controllo. XAML*.

4. Dal riquadro XAML, nella definizione dell'elemento di primo livello <xref:System.Windows.Controls.UserControl> , aggiungere la seguente dichiarazione di evento dopo le dichiarazioni dello spazio dei nomi.

    ```xml
    Loaded="OnLoaded"
    ```

5. Nel riquadro di progettazione fare clic sull'area principale del controllo e quindi premere **Canc**.

     Questo passaggio rimuove l' <xref:System.Windows.Controls.Border> elemento e tutti gli elementi al suo interno e lascia solo l'elemento di primo livello <xref:System.Windows.Controls.Grid> .

6. Dalla **casella degli strumenti** trascinare un <xref:System.Windows.Controls.StackPanel> controllo nella griglia.

7. Trascinare ora un oggetto <xref:System.Windows.Controls.TextBlock> , un oggetto <xref:System.Windows.Controls.TextBox> e un pulsante in <xref:System.Windows.Controls.StackPanel> .

8. Aggiungere un attributo **x:Name** per <xref:System.Windows.Controls.TextBox> e un `Click` evento per <xref:System.Windows.Controls.Button> , come illustrato nell'esempio seguente.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementare il controllo utente

1. Nel riquadro XAML, fare clic con il pulsante destro del mouse sull' `Click` attributo dell' <xref:System.Windows.Controls.Button> elemento, quindi scegliere **passa al gestore eventi**.

     Questo passaggio apre il *controllo. XAML. cs* e crea un gestore stub per l' `Button_Click` evento.

2. Aggiungere le seguenti `using` direttive all'inizio del file.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Aggiungere una `SettingsStore` proprietà privata, come illustrato nell'esempio seguente.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Questa proprietà ottiene innanzitutto un riferimento all' <xref:EnvDTE80.DTE2> interfaccia che contiene il modello a oggetti di automazione, dall'oggetto <xref:System.Windows.FrameworkElement.DataContext%2A> del controllo utente, quindi utilizza il DTE per ottenere un'istanza dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interfaccia. Quindi utilizza tale istanza per restituire le impostazioni utente correnti.

4. Compilare l' `Button_Click` evento come indicato di seguito.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     In questo modo il contenuto della casella di testo viene scritto in un campo "impostazione" in una raccolta "Impostazioni" nel registro di sistema. Se la raccolta non esiste, viene creata.

5. Aggiungere il seguente gestore per l' `OnLoaded` evento del controllo utente.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Questo codice imposta il testo della casella di testo sul valore corrente di "setting".

6. Compilare il controllo utente.

7. In **Esplora soluzioni** aprire *source. Extension. vsixmanifest*.

8. Nell'Editor manifesto impostare **nome prodotto** per **salvare la pagina iniziale impostazioni**.

     Questa funzionalità consente di impostare il nome della pagina iniziale in modo che venga visualizzato nell'elenco **Personalizza pagina iniziale** della finestra di dialogo **Opzioni** .

9. Compilare il file *StartPage. XAML*.

## <a name="test-the-control"></a>Testare il controllo

1. Premere **F5**.

     Si apre l'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, scegliere **Opzioni** dal menu **strumenti** .

3. Nel nodo **ambiente** , fare clic su **avvio**, quindi nell'elenco **Personalizza pagina iniziale** selezionare **[estensione installata] Salva impostazioni di avvio pagina**.

     Fare clic su **OK**.

4. Chiudere la pagina iniziale, se è aperta, quindi scegliere **pagina iniziale** dal menu **Visualizza** .

5. Nella pagina iniziale fare clic sulla scheda **controllo** .

6. Nella casella di testo digitare **Cat**, quindi fare clic su **Salva impostazione**.

7. Chiudere la pagina iniziale, quindi riaprirla.

     La parola "Cat" deve essere visualizzata nella casella di testo.

8. Sostituire la parola "Cat" con la parola "Dog". Non fare clic sul pulsante.

9. Chiudere la pagina iniziale, quindi riaprirla.

     La parola "Dog" deve essere visualizzata nella casella di testo, anche se l'impostazione non è stata salvata perché Visual Studio mantiene le finestre degli strumenti in memoria, anche se sono chiuse, fino a quando non si chiude Visual Studio.

10. Chiudere l'istanza sperimentale di Visual Studio.

11. Premere **F5** per riaprire l'istanza sperimentale.

12. La parola "Cat" deve essere visualizzata nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi

È possibile modificare questo controllo utente per salvare e recuperare un numero qualsiasi di impostazioni personalizzate utilizzando valori diversi di gestori eventi diversi per ottenere e impostare la `SettingsStore` Proprietà. Finché si usa un `propertyName` parametro diverso per ogni chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , i valori non vengono sovrascritti tra loro nel registro di sistema.

## <a name="see-also"></a>Vedi anche

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
