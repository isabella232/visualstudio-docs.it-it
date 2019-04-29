---
title: 'Procedura dettagliata: Salvataggio delle impostazioni utente in una pagina di avvio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2362bda715a95e4228b6e4f882f1f8fb708667dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62964781"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Procedura dettagliata: Salvare le impostazioni utente in una pagina iniziale

È possibile rendere persistenti le impostazioni utente per la pagina iniziale. Seguendo questa procedura dettagliata, è possibile creare un controllo per salvare un'impostazione nel Registro di sistema quando l'utente fa clic su un pulsante e quindi recupera impostata ogni volta che viene caricata la pagina iniziale. Poiché il modello di progetto di pagina iniziale include un controllo utente personalizzabile, e il valore predefinito avviare pagina XAML chiama tale controllo, non è necessario modificare la pagina iniziale di se stesso.

L'archivio delle impostazioni che viene creata un'istanza di questa procedura dettagliata è un'istanza del <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interfaccia, che legge e scrive nel percorso seguente del Registro di sistema quando viene chiamata: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<CollectionName>**

Quando è in esecuzione nell'istanza sperimentale di Visual Studio, l'archivio delle impostazioni legge e scrive **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<NomeRaccolta >.**

Per altre informazioni su come mantenere le impostazioni, vedere [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> È possibile scaricare il modello di progetto di pagina iniziale usando **gestore estensioni del**.

## <a name="set-up-the-project"></a>Configurare il progetto

1. Creare un progetto di pagina iniziale come descritto in [creare una pagina iniziale personalizzata](creating-a-custom-start-page.md). Denominare il progetto **SaveMySettings**.

2. Nelle **Esplora soluzioni**, aggiungere i riferimenti assembly seguenti al progetto StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Aprire *MyControl*.

4. Nel riquadro di XAML, di primo livello <xref:System.Windows.Controls.UserControl> definizione dell'elemento, aggiungere la seguente dichiarazione di eventi dopo le dichiarazioni dello spazio dei nomi.

    ```xml
    Loaded="OnLoaded"
    ```

5. Nel riquadro di progettazione, fare clic sull'area principale del controllo e quindi premere **Elimina**.

     Questo passaggio rimuove il <xref:System.Windows.Controls.Border> elemento e tutti gli elementi in essa contenuti, lasciando solo i primi a livello <xref:System.Windows.Controls.Grid> elemento.

6. Dal **casella degli strumenti**, trascinare un <xref:System.Windows.Controls.StackPanel> controllo alla griglia.

7. Trascinare ora una <xref:System.Windows.Controls.TextBlock>, una <xref:System.Windows.Controls.TextBox>e un pulsante per la <xref:System.Windows.Controls.StackPanel>.

8. Aggiungere un **X:Name** dell'attributo per il <xref:System.Windows.Controls.TextBox>e un `Click` evento per il <xref:System.Windows.Controls.Button>, come illustrato nell'esempio seguente.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementare il controllo utente

1. Nel riquadro di XAML, fare doppio clic il `Click` attributo del <xref:System.Windows.Controls.Button> elemento e quindi fare clic su **passa al gestore eventi**.

     Questo passaggio apre *MyControl.xaml.cs*e crea un gestore di stub per il `Button_Click` evento.

2. Aggiungere il codice seguente `using` istruzioni all'inizio del file.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Aggiungere una privata `SettingsStore` proprietà, come illustrato nell'esempio seguente.

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

     Questa proprietà ottiene innanzitutto un riferimento al <xref:EnvDTE80.DTE2> interfaccia, che contiene il modello oggetto di automazione, a partire dal <xref:System.Windows.FrameworkElement.DataContext%2A> del controllo utente e quindi Usa l'oggetto DTE per ottenere un'istanza del <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interfaccia. Usa quindi tale istanza per restituire le impostazioni utente correnti.

4. Compilare il `Button_Click` evento come indicato di seguito.

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

     Scrive il contenuto della casella di testo a un campo "MySetting" in una raccolta di "impostazioni personali" nel Registro di sistema. Se la raccolta non esiste, viene creato.

5. Aggiungere il gestore seguente per il `OnLoaded` eventi del controllo utente.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Questo codice imposta il testo della casella di testo per il valore corrente della "MySetting".

6. Compilare il controllo utente.

7. Nelle **Esplora soluzioni**aprire *vsixmanifest*.

8. Nell'editor del manifesto, impostare **Product Name** al **Salva pagina di avvio impostazioni personali**.

     Questa funzione imposta il nome della pagina iniziale come verrà visualizzato nei **Personalizza pagina iniziale** nell'elenco il **opzioni** nella finestra di dialogo.

9. Compilare *StartPage*.

## <a name="test-the-control"></a>Testare il controllo

1. Premere **F5**.

     Apre l'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, sul **degli strumenti** menu, fare clic su **opzioni**.

3. Nel **ambiente** nodo, fare clic su **avvio**, quindi il **Personalizza pagina iniziale** elenco, selezionare **[estensione installata] Salva My le impostazioni di pagina iniziale** .

     Fare clic su **OK**.

4. Chiudere la pagina iniziale se è aperto, quindi scegliere il **vista** menu, fare clic su **pagina Start**.

5. Nella pagina Start, scegliere il **MyControl** scheda.

6. Nella casella di testo, digitare **Cat**, quindi fare clic su **Salva My impostazione**.

7. Chiudere la pagina iniziale e quindi aprirlo nuovamente.

     La parola "Cat" deve essere visualizzato nella casella di testo.

8. Sostituire la parola "Cat" con la parola "Dog". Non fare clic sul pulsante.

9. Chiudere la pagina iniziale e quindi aprirlo nuovamente.

     La parola "Dog" deve essere visualizzata nella casella di testo, anche se non sono state salvate le impostazioni perché Visual Studio mantiene finestre degli strumenti in memoria, anche qualora siano chiusi, fino a quando non si chiude Visual Studio stesso.

10. Chiudere l'istanza sperimentale di Visual Studio.

11. Premere **F5** per riaprire l'istanza sperimentale.

12. La parola "Cat" deve essere visualizzato nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi

È possibile modificare questo controllo utente per salvare e recuperare un numero qualsiasi di impostazioni personalizzate utilizzando valori diversi dai gestori eventi diversi per ottenere e impostare il `SettingsStore` proprietà. Purché si utilizzino un diverso `propertyName` parametro per ogni chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, i valori non sovrascriveranno tra loro nel Registro di sistema.

## <a name="see-also"></a>Vedere anche

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)