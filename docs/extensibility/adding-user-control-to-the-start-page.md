---
title: Aggiunta del controllo utente alla pagina iniziale Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740124"
---
# <a name="add-user-control-to-the-start-page"></a>Aggiungere il controllo utente alla pagina inizialeAdd user control to the Start Page

In questa procedura dettagliata viene illustrato come aggiungere un riferimento DLL a una pagina iniziale personalizzata. L'esempio aggiunge un controllo utente alla soluzione, compila il controllo utente e quindi fa riferimento all'assembly compilato dal file *XAML* della pagina iniziale. Una nuova scheda ospita il controllo utente, che funziona come un browser Web di base.

È possibile usare lo stesso processo per aggiungere qualsiasi assembly che può essere chiamato da un file *XAML.*

## <a name="add-a-wpf-user-control-to-the-solution"></a>Aggiungere un controllo utente WPF alla soluzioneAdd a WPF user control to the solution

Aggiungere innanzitutto un controllo utente Windows Presentation Foundation (WPF) alla soluzione della pagina iniziale.

1. Creare una pagina iniziale utilizzando creata in [Creare una pagina iniziale personalizzata.](../extensibility/creating-a-custom-start-page.md)

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione, **scegliere Aggiungi**, quindi Nuovo **progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere il nodo **Visual Basic** o **Visual C,** quindi fare clic su **Windows**. Nel riquadro centrale selezionare **Libreria di controlli utente WPF**.

4. Assegnare `WebUserControl` un nome al controllo, quindi scegliere **OK**.

## <a name="implement-the-user-control"></a>Implementare il controllo utente

Per implementare un controllo utente WPFWPF, compilare l'interfaccia utente (UI) in XAML e quindi scrivere gli eventi code-behind in C 'NET o in un altro linguaggio .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Per scrivere il codice XAML per il controllo utenteTo write the XAML for the user control

1. Aprire il file XAML per il controllo utente. Nell'elemento `<Grid>` aggiungere le definizioni di riga seguenti al controllo.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Nell'elemento `<Grid>` principale aggiungere il `<Grid>` nuovo elemento seguente, che contiene una casella di testo per digitare gli indirizzi Web e un pulsante per l'impostazione del nuovo indirizzo.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Aggiungere la cornice seguente all'elemento di primo livello `<Grid>` subito dopo l'elemento `<Grid>` che contiene il pulsante e la casella di testo.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Nell'esempio seguente viene illustrato il codice XAML completato per il controllo utente.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Per scrivere gli eventi code-behind per il controllo utenteTo write the code-behind events for the user control

1. Nella finestra di progettazione XAML fare doppio clic sul pulsante **Imposta indirizzo** aggiunto al controllo.

    Il file *UserControl1.cs* verrà aperto nell'editor di codice.

2. Compilare il SetButton_Click gestore eventi come indicato di seguito.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Questo codice imposta l'indirizzo Web digitato nella casella di testo come destinazione per il browser Web. Se l'indirizzo non è valido, il codice genera un errore.

3. È inoltre necessario gestire l'evento WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Compilare la soluzione.

## <a name="add-the-user-control-to-the-start-page"></a>Aggiungere il controllo utente alla pagina iniziale

Per rendere questo controllo disponibile per il progetto di pagina iniziale, nel file di progetto di pagina iniziale, aggiungere un riferimento alla nuova libreria di controlli. È quindi possibile aggiungere il controllo al markup XAML della pagina iniziale.

1. In **Esplora soluzioni**, nel progetto di pagina iniziale fare clic con il pulsante destro del mouse su **Riferimenti,** quindi **scegliere Aggiungi riferimento**.

2. Nella scheda **Progetti** selezionare **WebUserControl** e quindi fare clic su **OK**.

3. Nel menu **Compila** scegliere **Compila soluzione**.

    La compilazione della soluzione rende il controllo utente disponibile per IntelliSense per altri file nella soluzione.

    Per aggiungere il controllo al markup XAML della pagina iniziale, aggiungi un riferimento allo spazio dei nomi all'assembly, quindi inserisci il controllo nella pagina.

### <a name="to-add-the-control-to-the-markup"></a>Per aggiungere il controllo al markup

1. In **Esplora soluzioni**aprire il file *XAML* della pagina iniziale.

2. Nel riquadro **XAML** aggiungere la dichiarazione dello <xref:System.Windows.Controls.Grid> spazio dei nomi seguente all'elemento di primo livello.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. Nel riquadro **XAML** scorrere \<fino alla sezione Griglia>.

    La sezione <xref:System.Windows.Controls.TabControl> contiene un <xref:System.Windows.Controls.Grid> elemento in un elemento.

4. Aggiungere \<un elemento tabControl \<> contenente un oggetto TabItem> che contiene un riferimento al controllo utente.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    A questo punto è possibile testare il controllo.

## <a name="test-a-manually-created-custom-start-page"></a>Testare una pagina iniziale personalizzata creata manualmente

1. Copiare il file XAML e tutti i file di testo o di markup di supporto nella cartella *%USERPROFILE%.\\ *

2. Se la pagina iniziale fa riferimento a controlli o tipi in assembly non installati da Visual Studio, copiare gli assembly e quindi incollarli nella cartella di installazione di _Visual Studio,_**ovvero Common7, IDE, PrivateAssemblies\\**.

3. Al prompt dei comandi di Visual Studio digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.

4. Nell'istanza sperimentale, **vai alla** > pagina Strumenti**Opzioni** > di**avvio** dell'ambiente**Environment** > e seleziona il file XAML dall'elenco a discesa Personalizza **pagina iniziale.**

5. Scegliere **Pagina iniziale** dal menu **Visualizza**.

    Verrà visualizzata la pagina iniziale personalizzata. Se si desidera modificare i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi riaprire l'istanza sperimentale per visualizzare le modifiche.

## <a name="see-also"></a>Vedere anche

- [Controlli contenitore WPFWPF container controls](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Procedura dettagliata: Aggiungere codice XAML personalizzato alla pagina inizialeWalkthrough: Add custom XAML to the Start Page](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
