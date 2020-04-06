---
title: 'Procedura dettagliata: salvataggio delle impostazioni utente in una pagina iniziale Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697089"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Procedura dettagliata: Salvare le impostazioni utente in una pagina inizialeWalkthrough: Save user settings on a Start Page

È possibile rendere persistenti le impostazioni utente per la pagina iniziale. Seguendo questa procedura dettagliata, è possibile creare un controllo che salva un'impostazione nel Registro di sistema quando l'utente fa clic su un pulsante e quindi recupera tale impostazione ogni volta che viene caricata la pagina iniziale. Poiché il modello di progetto di pagina iniziale include un controllo utente personalizzabile e il codice XAML della pagina iniziale predefinito chiama tale controllo, non è necessario modificare la pagina iniziale stessa.

L'archivio delle impostazioni di cui viene <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> creata un'istanza in questa procedura dettagliata è un'istanza dell'interfaccia, che legge e scrive nel seguente percorso del Registro di sistema quando viene chiamato: **HKCU, Software, Microsoft .NET Framework 14.0\\\<CollectionName>**

Quando è in esecuzione nell'istanza sperimentale di Visual Studio, l'archivio delle impostazioni legge e scrive **in\\\<HKCU Software Microsoft VisualStudio 14.0Exp CollectionName>.**

Per ulteriori informazioni su come rendere persistenti le impostazioni, vedere [Estensione delle impostazioni e](../extensibility/extending-user-settings-and-options.md)delle opzioni utente .

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> È possibile scaricare il modello di progetto Pagina iniziale utilizzando **Gestione estensioni**.

## <a name="set-up-the-project"></a>Configurare il progetto

1. Creare un progetto di pagina iniziale come descritto in [Creare una pagina iniziale personalizzata](creating-a-custom-start-page.md). Assegnare al progetto il nome **SaveMySettings**.

2. In **Esplora soluzioni**aggiungere i seguenti riferimenti all'assembly al progetto StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Aprire *MyControl.xaml*.

4. Nel riquadro XAML, nella <xref:System.Windows.Controls.UserControl> definizione dell'elemento di primo livello, aggiungere la dichiarazione di evento seguente dopo le dichiarazioni dello spazio dei nomi.

    ```xml
    Loaded="OnLoaded"
    ```

5. Nel riquadro di progettazione fare clic sull'area principale del controllo e quindi premere **CANC.**

     Questo passaggio <xref:System.Windows.Controls.Border> rimuove l'elemento e tutti gli <xref:System.Windows.Controls.Grid> elementi in esso e lascia solo l'elemento di primo livello.

6. Dalla **Casella degli** <xref:System.Windows.Controls.StackPanel> strumenti trascinare un controllo nella griglia.

7. Ora trascinare <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox>un , a <xref:System.Windows.Controls.StackPanel>e un Button al .

8. Aggiungere un attributo **x:Name** per il <xref:System.Windows.Controls.TextBox>metodo , e un `Click` evento per il <xref:System.Windows.Controls.Button>, come illustrato nell'esempio seguente.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementare il controllo utente

1. Nel riquadro XAML fare `Click` clic con <xref:System.Windows.Controls.Button> il pulsante destro del mouse sull'attributo dell'elemento e quindi **scegliere Passa al gestore eventi**.

     Questo passaggio apre *MyControl.xaml.cs*e crea `Button_Click` un gestore stub per l'evento.

2. Aggiungere le `using` direttive seguenti all'inizio del file.

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

     Questa proprietà ottiene innanzitutto <xref:EnvDTE80.DTE2> un riferimento all'interfaccia, che <xref:System.Windows.FrameworkElement.DataContext%2A> contiene il modello a oggetti di automazione, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> dal controllo utente e quindi utilizza il DTE per ottenere un'istanza dell'interfaccia. Quindi utilizza tale istanza per restituire le impostazioni utente correnti.

4. Compilare `Button_Click` l'evento come segue.

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

     In questo modo il contenuto della casella di testo viene scritto in un campo "MySetting" in una raccolta "MySettings" nel Registro di sistema. Se la raccolta non esiste, viene creata.

5. Aggiungere il gestore `OnLoaded` seguente per l'evento del controllo utente.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Questo codice imposta il testo della casella di testo sul valore corrente di "MySetting".

6. Compilare il controllo utente.

7. In **Esplora soluzioni**aprire *source.extension.vsixmanifest*.

8. Nell'editor del manifesto impostare **Nome prodotto** su Salva **pagina iniziale impostazioni personali**.

     Questa funzionalità imposta il nome della pagina iniziale così come viene visualizzata nell'elenco **Personalizza pagina iniziale** della finestra di dialogo **Opzioni.**

9. Compilare *StartPage.xaml*.

## <a name="test-the-control"></a>Testare il controllo

1. Premere **F5**.

     Verrà aperta l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio opens.

2. Nell'istanza sperimentale scegliere **Opzioni**dal menu **Strumenti** .

3. Nel nodo **Ambiente** fare clic su **Avvio**e quindi nell'elenco **Personalizza pagina iniziale** selezionare **[Estensione installata] Salva pagina iniziale impostazioni personali**.

     Fare clic su **OK**.

4. Chiudere la pagina iniziale, se aperta, quindi scegliere **Pagina iniziale**dal menu **Visualizza** .

5. Nella pagina iniziale fare clic sulla scheda **MyControl.**

6. Nella casella di testo digitare **Cat**e quindi fare clic su **Salva impostazioni**personali .

7. Chiudere la pagina iniziale e riaprirla.

     La parola "Cat" dovrebbe essere visualizzata nella casella di testo.

8. Sostituire la parola "Cat" con la parola "Dog". Non fare clic sul pulsante.

9. Chiudere la pagina iniziale e riaprirla.

     La parola "Dog" deve essere visualizzata nella casella di testo, anche se non è stata salvata l'impostazione perché Visual Studio mantiene le finestre degli strumenti in memoria, anche se sono chiuse, fino a quando Visual Studio stesso si chiude.

10. Chiudere l'istanza sperimentale di Visual Studio.

11. Premere **F5** per riaprire l'istanza sperimentale.

12. La parola "Cat" dovrebbe essere visualizzata nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi

È possibile modificare questo controllo utente per salvare e recuperare un numero qualsiasi di impostazioni `SettingsStore` personalizzate utilizzando valori diversi da gestori eventi diversi per ottenere e impostare la proprietà . Se si utilizza un `propertyName` parametro diverso <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>per ogni chiamata a , i valori non si sovrascrivono reciprocamente nel Registro di sistema.

## <a name="see-also"></a>Vedere anche

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Aggiunta di comandi di Visual Studio a una pagina inizialeAdding Visual Studio commands to a Start Page](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
