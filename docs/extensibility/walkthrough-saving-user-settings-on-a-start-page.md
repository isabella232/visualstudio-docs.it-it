---
title: 'Procedura dettagliata: Salvataggio di Impostazioni utente in una pagina iniziale | Microsoft Docs'
description: Informazioni su come rendere persistenti le impostazioni utente per la pagina iniziale salvando un'impostazione nel Registro di sistema usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3f312bb9b62ebbcc694a64ad485d19ca628b1e8e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634483"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Procedura dettagliata: Salvare le impostazioni utente in una pagina iniziale

È possibile rendere persistenti le impostazioni utente per la pagina iniziale. Seguendo questa procedura dettagliata, è possibile creare un controllo che salva un'impostazione nel Registro di sistema quando l'utente fa clic su un pulsante e quindi recupera tale impostazione ogni volta che viene caricata la pagina iniziale. Poiché il modello di progetto Pagina iniziale include un controllo utente personalizzabile e il codice XAML della pagina iniziale predefinito chiama tale controllo, non è necessario modificare la pagina iniziale stessa.

L'archivio impostazioni di cui viene creata un'istanza in questa procedura dettagliata è un'istanza dell'interfaccia che legge e scrive nel percorso del Registro di sistema seguente quando viene <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> chiamato: **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName>**

Quando è in esecuzione nell'istanza sperimentale di Visual Studio, l'archivio impostazioni legge e scrive in **HKCU\Software\Microsoft\VisualStudio\14.0Exp. \\ \<CollectionName>**

Per altre informazioni su come rendere persistenti le impostazioni, vedere [Estensione delle impostazioni utente Impostazioni opzioni](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)
>
> È possibile scaricare il modello di progetto Pagina iniziale usando **Gestione estensioni**.

## <a name="set-up-the-project"></a>Configurare il progetto

1. Creare un progetto di pagina iniziale come descritto in [Creare una pagina iniziale personalizzata.](creating-a-custom-start-page.md) Assegnare al progetto **il nome SaveMySettings**.

2. In **Esplora soluzioni** aggiungere i riferimenti agli assembly seguenti al progetto StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Aprire *MyControl.xaml.*

4. Nella definizione dell'elemento di primo livello del riquadro XAML aggiungere la dichiarazione di <xref:System.Windows.Controls.UserControl> evento seguente dopo le dichiarazioni dello spazio dei nomi.

    ```xml
    Loaded="OnLoaded"
    ```

5. Nel riquadro di progettazione fare clic sull'area principale del controllo e quindi premere **CANC.**

     Questo passaggio rimuove l'elemento e tutti gli elementi in <xref:System.Windows.Controls.Border> esso presenti e lascia solo l'elemento di primo <xref:System.Windows.Controls.Grid> livello.

6. Dalla Casella **degli strumenti** trascinare un controllo <xref:System.Windows.Controls.StackPanel> nella griglia.

7. Trascinare ora <xref:System.Windows.Controls.TextBlock> un oggetto , un oggetto e un pulsante in <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.StackPanel> .

8. Aggiungere un **attributo x:Name** per <xref:System.Windows.Controls.TextBox> e un evento per , come illustrato `Click` <xref:System.Windows.Controls.Button> nell'esempio seguente.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementare il controllo utente

1. Nel riquadro XAML fare clic con il pulsante destro del mouse sull'attributo dell'elemento e quindi scegliere `Click` Passa al gestore <xref:System.Windows.Controls.Button> **eventi**.

     Questo passaggio apre *MyControl.xaml.cs* e crea un gestore stub per `Button_Click` l'evento.

2. Aggiungere le `using` direttive seguenti all'inizio del file.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs" id="Snippet11":::

3. Aggiungere una proprietà `SettingsStore` privata, come illustrato nell'esempio seguente.

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

     Questa proprietà ottiene prima un riferimento all'interfaccia , che contiene il modello a oggetti di Automazione, dal controllo utente e quindi usa la DTE per ottenere un'istanza <xref:EnvDTE80.DTE2> <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> dell'interfaccia. Usa quindi tale istanza per restituire le impostazioni utente correnti.

4. Compilare `Button_Click` l'evento come indicato di seguito.

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

     Il contenuto della casella di testo viene scritto in un campo "MySetting" in una raccolta "MySettings" nel Registro di sistema. Se la raccolta non esiste, viene creata.

5. Aggiungere il gestore seguente per `OnLoaded` l'evento del controllo utente.

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

7. In **Esplora soluzioni** aprire *source.extension.vsixmanifest*.

8. Nell'editor del manifesto impostare **Product Name** su Save My Impostazioni Start Page (Salva il Impostazioni **iniziale).**

     Questa funzionalità imposta il nome della pagina iniziale così come deve essere visualizzata nell'elenco **Personalizza pagina iniziale** nella finestra di **dialogo** Opzioni .

9. Compilare *StartPage.xaml.*

## <a name="test-the-control"></a>Testare il controllo

1. Premere **F5**.

     Viene aperta l'istanza sperimentale Visual Studio.

2. Nell'istanza sperimentale scegliere Opzioni **dal** menu **Strumenti**.

3. Nel nodo **Ambiente** fare clic su **Avvio** e quindi nell'elenco Personalizza pagina **iniziale** selezionare **[Estensione installata]** Salva Impostazioni pagina iniziale .

     Fare clic su **OK**.

4. Chiudere la pagina iniziale, se aperta, quindi scegliere Pagina **iniziale dal** **menu** Visualizza .

5. Nella pagina iniziale fare clic sulla **scheda MyControl.**

6. Nella casella di testo digitare **Cat** e quindi fare clic **su Salva impostazione.**

7. Chiudere la pagina iniziale e quindi aprirla di nuovo.

     La parola "Cat" deve essere visualizzata nella casella di testo.

8. Sostituire la parola "Cat" con la parola "Dog". Non fare clic sul pulsante.

9. Chiudere la pagina iniziale e quindi aprirla di nuovo.

     La parola "Cane" deve essere visualizzata nella casella di testo, anche se l'impostazione non è stata salvata perché Visual Studio mantiene le finestre degli strumenti in memoria, anche se sono chiuse, fino alla chiusura dell'Visual Studio stessa.

10. Chiudere l'istanza sperimentale di Visual Studio.

11. Premere **F5 per** riaprire l'istanza sperimentale.

12. La parola "Cat" deve essere visualizzata nella casella di testo.

## <a name="next-steps"></a>Passaggi successivi

È possibile modificare questo controllo utente per salvare e recuperare un numero qualsiasi di impostazioni personalizzate usando valori diversi da gestori eventi diversi per ottenere e impostare la `SettingsStore` proprietà . Se si usa un parametro diverso per ogni chiamata a , i valori non si sovrascrivono `propertyName` <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> l'un l'altro nel Registro di sistema.

## <a name="see-also"></a>Vedi anche

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Aggiunta Visual Studio comandi a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
