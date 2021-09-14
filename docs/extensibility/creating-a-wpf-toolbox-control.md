---
title: Creazione di un controllo della casella degli strumenti WPF | Microsoft Docs
description: Informazioni su come usare il modello Controllo casella degli strumenti WPF per creare un controllo della casella degli strumenti che è possibile distribuire ad altri utenti.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6bf8dae61373b8a9ba5814930298896f3ba41da6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627695"
---
# <a name="create-a-wpf-toolbox-control"></a>Creare un controllo della casella degli strumenti WPF

Il modello controllo casella degli strumenti WPF (Windows Presentation Framework) consente  di creare controlli WPF che vengono aggiunti automaticamente alla casella degli strumenti quando viene installata l'estensione. Questa procedura dettagliata illustra come usare il modello per creare **un** controllo della casella degli strumenti che è possibile distribuire ad altri utenti.

A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-toolbox-control"></a>Creare il controllo della casella degli strumenti

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Creare un'estensione con un controllo della casella degli strumenti WPF

1. Creare un progetto VSIX denominato `MyToolboxControl` . È possibile trovare il modello di progetto VSIX nella finestra **di dialogo Nuovo Project** ricerca di "vsix".

2. Quando si apre il progetto, aggiungere un modello di elemento **controllo della casella** degli strumenti WPF denominato `MyToolboxControl` . Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Nella finestra **di dialogo Aggiungi nuovo elemento** passare a **Estendibilità di Visual C#**  >   e selezionare Controllo casella degli **strumenti WPF**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *MyToolboxControl.cs*.

    La soluzione contiene ora un controllo utente, un oggetto che aggiunge il controllo alla casella degli strumenti e una voce `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> **Microsoft.VisualStudio.ToolboxControl** Asset nel manifesto VSIX per la distribuzione.

#### <a name="to-create-the-control-ui"></a>Creare l'interfaccia utente del controllo

1. Aprire *MyToolboxControl.xaml* nella finestra di progettazione.

    La finestra di progettazione mostra un controllo <xref:System.Windows.Controls.Grid> che contiene un controllo <xref:System.Windows.Controls.Button>.

2. Disporre il layout della griglia. Quando si seleziona il controllo, le barre di controllo blu vengono visualizzate sui bordi <xref:System.Windows.Controls.Grid> superiore e sinistro della griglia. È possibile aggiungere righe e colonne alla griglia facendo clic sulle barre.

3. Aggiungere controlli figlio alla griglia. È possibile posizionare un controllo figlio  trascinandolo dalla casella degli strumenti a una sezione della griglia o impostandone gli attributi `Grid.Row` e nel codice `Grid.Column` XAML. Nell'esempio seguente vengono aggiunte due etichette nella riga superiore della griglia e un pulsante nella seconda riga.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Ridenominazione del controllo

 Per impostazione predefinita, il controllo verrà visualizzato nella casella degli **strumenti** **come MyToolboxControl** in un gruppo denominato **MyToolboxControl.MyToolboxControl**. È possibile modificare questi nomi nel file *MyToolboxControl.xaml.cs.*

1. Aprire *MyToolboxControl.xaml.cs* nella visualizzazione codice.

2. Trovare la `MyToolboxControl` classe e rinominarla in TestControl. Il modo più rapido per eseguire questa operazione è rinominare la classe, quindi selezionare **Rinomina** dal menu di scelta rapida e completare i passaggi. Per altre informazioni sul **comando Rename,** vedere [Rename refactoring (C#) (Ridenominazione del refactoring (C#)](../ide/reference/rename.md).

3. Passare `ProvideToolboxControl` all'attributo e modificare il valore del primo parametro in **Test**. Si tratta del nome del gruppo che conterrà il controllo nella casella degli **strumenti**.

    Il codice risultante dovrebbe essere simile al seguente:

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Compilazione, test e distribuzione

 Quando si esegue il debug del progetto, è necessario trovare il controllo installato nella casella **degli** strumenti dell'istanza sperimentale di Visual Studio.

### <a name="to-build-and-test-the-control"></a>Per compilare e testare il controllo

1. Ricompilare il progetto e avviare il debug.

2. Nella nuova istanza di Visual Studio creare un progetto di applicazione WPF. Assicurarsi che il finestra di progettazione XAML sia aperto.

3. Individuare il controllo nella **casella degli strumenti** e trascinarlo nell'area di progettazione.

4. Avviare il debug dell'applicazione WPF.

5. Verificare che il controllo sia visualizzato.

### <a name="to-deploy-the-control"></a>Per distribuire il controllo

1. Dopo aver compilato il progetto testato, è possibile trovare il file *vsix* nella cartella *\bin\debug \* del progetto.

2. È possibile installarlo in un computer locale facendo doppio clic sul file con estensione *vsix* e seguendo la procedura di installazione. Per disinstallare il controllo, passare **a** Estensioni e aggiornamenti degli strumenti e cercare  >   l'estensione del controllo, quindi fare clic su **Disinstalla**.

3. Upload il file *vsix* in una rete o in un sito Web.

    Se si carica il file nel sito Web [di Visual Studio Marketplace,](https://marketplace.visualstudio.com/) altri utenti possono usare le estensioni e gli aggiornamenti degli strumenti in Visual Studio per trovare il controllo online e   >   installarlo.
