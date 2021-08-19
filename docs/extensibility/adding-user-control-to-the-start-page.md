---
title: Aggiunta del controllo utente alla pagina iniziale | Microsoft Docs
description: Informazioni su come aggiungere un controllo Windows Presentation Foundation (WPF) alla pagina iniziale in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 794ff65d58e03b22584f0a4d2a291371b1e08c81
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120556"
---
# <a name="add-user-control-to-the-start-page"></a>Aggiungere il controllo utente alla pagina iniziale

Questa procedura dettagliata illustra come aggiungere un riferimento DLL a una pagina iniziale personalizzata. L'esempio aggiunge un controllo utente alla soluzione, compila il controllo utente e quindi fa riferimento all'assembly compilato dal file con estensione xaml della *pagina* iniziale. Una nuova scheda ospita il controllo utente, che funziona come base Web browser.

È possibile usare lo stesso processo per aggiungere qualsiasi assembly che può essere chiamato da un file *con estensione xaml.*

## <a name="add-a-wpf-user-control-to-the-solution"></a>Aggiungere un controllo utente WPF alla soluzione

Aggiungere prima di tutto un Windows Presentation Foundation utente (WPF) alla soluzione Pagina iniziale.

1. Creare una pagina iniziale usando è stata creata in [Creare una pagina iniziale personalizzata.](../extensibility/creating-a-custom-start-page.md)

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione, scegliere Aggiungi **e** quindi fare clic su **Nuovo Project**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo Project** espandere il nodo Visual Basic **o Visual C#** e fare clic **su** Windows .  Nel riquadro centrale selezionare **Libreria di controlli utente WPF**.

4. Assegnare al controllo il `WebUserControl` nome e quindi fare clic su **OK.**

## <a name="implement-the-user-control"></a>Implementare il controllo utente

Per implementare un controllo utente WPF, compilare l'interfaccia utente in XAML e quindi scrivere gli eventi code-behind in C# o in un altro linguaggio .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Per scrivere il codice XAML per il controllo utente

1. Aprire il file XAML per il controllo utente. `<Grid>`Nell'elemento aggiungere le definizioni di riga seguenti al controllo .

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Nell'elemento main aggiungere il nuovo elemento seguente, che contiene una casella di testo per digitare indirizzi Web e un pulsante per `<Grid>` `<Grid>` impostare il nuovo indirizzo.

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

3. Aggiungere il frame seguente all'elemento di primo `<Grid>` livello subito dopo `<Grid>` l'elemento che contiene il pulsante e la casella di testo.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. L'esempio seguente mostra il codice XAML completato per il controllo utente.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Per scrivere gli eventi code-behind per il controllo utente

1. Nella finestra di progettazione XAML fare doppio clic sul **pulsante Imposta** indirizzo aggiunto al controllo.

    Il file *UserControl1.cs* viene aperto nell'editor di codice.

2. Compilare il gestore SetButton_Click eventi come indicato di seguito.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
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

    Questo codice imposta l'indirizzo Web digitato nella casella di testo come destinazione per l'Web browser. Se l'indirizzo non è valido, il codice genera un errore.

3. È anche necessario gestire l'WebFrame_Navigated seguente:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Compilare la soluzione.

## <a name="add-the-user-control-to-the-start-page"></a>Aggiungere il controllo utente alla pagina iniziale

Per rendere questo controllo disponibile per il progetto Pagina iniziale, nel file di progetto della pagina iniziale aggiungere un riferimento alla nuova libreria di controlli. È quindi possibile aggiungere il controllo al markup XAML della pagina iniziale.

1. In **Esplora soluzioni** nel progetto Pagina iniziale fare clic con il pulsante destro del mouse su **Riferimenti** e quindi scegliere **Aggiungi riferimento**.

2. Nella scheda **Progetti** selezionare **WebUserControl** e quindi fare clic su **OK.**

3. Nel menu **Compila** scegliere **Compila soluzione**.

    La compilazione della soluzione rende il controllo utente disponibile per IntelliSense per altri file nella soluzione.

    Per aggiungere il controllo al markup XAML della pagina iniziale, aggiungere un riferimento allo spazio dei nomi all'assembly e quindi inserire il controllo nella pagina.

### <a name="to-add-the-control-to-the-markup"></a>Per aggiungere il controllo al markup

1. In **Esplora soluzioni** aprire il file con estensione xaml della *pagina* iniziale.

2. Nel riquadro **XAML** aggiungere la dichiarazione dello spazio dei nomi seguente all'elemento di primo <xref:System.Windows.Controls.Grid> livello.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. Nel riquadro **XAML** scorrere fino alla \<Grid> sezione .

    La sezione contiene un <xref:System.Windows.Controls.TabControl> elemento in un elemento <xref:System.Windows.Controls.Grid> .

4. Aggiungere un \<TabControl> elemento contenente un oggetto contenente un riferimento al controllo \<TabItem> utente.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    È ora possibile testare il controllo.

## <a name="test-a-manually-created-custom-start-page"></a>Testare una pagina iniziale personalizzata creata manualmente

1. Copiare il file XAML e tutti i file di testo o di markup di supporto nella cartella *%USERPROFILE%\Documenti\Visual Studio 2015\StartPages. \\*

2. Se la pagina iniziale fa riferimento a controlli o tipi negli assembly non installati da Visual Studio, copiare gli assembly e incollarli nella cartella di installazione di _Visual Studio_**\Common7\IDE\PrivateAssemblies \\**.

3. Al prompt Visual Studio comando digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.

4. Nell'istanza sperimentale passare alla pagina **Avvio** ambiente opzioni strumenti  >    >    >   e selezionare il file XAML nell'elenco a discesa **Personalizza pagina iniziale.**

5. Scegliere **Pagina iniziale** dal menu **Visualizza**.

    Verrà visualizzata la pagina iniziale personalizzata. Per modificare i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi ria aprire l'istanza sperimentale per visualizzare le modifiche.

## <a name="see-also"></a>Vedi anche

- [Controlli contenitore WPF](/previous-versions/bb675291(v=vs.110))
- [Procedura dettagliata: Aggiungere codice XAML personalizzato alla pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)