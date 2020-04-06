---
title: Creazione di un controllo della casella degli strumenti WPF Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739574"
---
# <a name="create-a-wpf-toolbox-control"></a>Creare un controllo della casella degli strumenti WPFCreate a WPF Toolbox Control

Il WPF (Windows Presentation Framework) modello di controllo della casella degli strumenti consente di creare controlli WPF che vengono aggiunti automaticamente alla **casella degli strumenti** quando viene installata l'estensione. In questa procedura dettagliata viene illustrato come utilizzare il modello per creare un controllo **della casella degli strumenti** che è possibile distribuire ad altri utenti.

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-toolbox-control"></a>Creare il controllo della casella degli strumentiCreate the Toolbox Control

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Creare un'estensione con un controllo della casella degli strumenti WPFCreate an extension with a WPF Toolbox Control

1. Creare un progetto `MyToolboxControl`VSIX denominato . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".

2. Quando si apre il progetto, aggiungere `MyToolboxControl`un modello di elemento Controllo casella degli strumenti **WPF** denominato . In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a**Estensibilità** **di Visual C,** > quindi selezionare **Controllo casella degli strumenti WPF**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *MyToolboxControl.cs*.

    La soluzione contiene ora un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> controllo utente, un che aggiunge il controllo alla **casella degli strumenti**e una voce **Microsoft.VisualStudio.ToolboxControl** Asset nel manifesto VSIX per la distribuzione.

#### <a name="to-create-the-control-ui"></a>Creare l'interfaccia utente del controllo

1. Aprire *MyToolboxControl.xaml* nella finestra di progettazione.

    La finestra di progettazione mostra un controllo <xref:System.Windows.Controls.Grid> che contiene un controllo <xref:System.Windows.Controls.Button>.

2. Disporre il layout della griglia. Quando si <xref:System.Windows.Controls.Grid> seleziona il controllo, le barre di controllo blu vengono visualizzate sui bordi superiore e sinistro della griglia. È possibile aggiungere righe e colonne alla griglia facendo clic sulle barre.

3. Aggiungere controlli figlio alla griglia. È possibile posizionare un controllo figlio trascinandolo dalla **Casella degli** strumenti `Grid.Row` `Grid.Column` in una sezione della griglia oppure impostandone gli attributi e nel codice XAML. Nell'esempio seguente vengono aggiunte due etichette nella riga superiore della griglia e un pulsante nella seconda riga.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Ridenominazione del controllo

 Per impostazione predefinita, il controllo verrà visualizzato nella **Casella degli strumenti** come **MyToolboxControl** in un gruppo denominato **MyToolboxControl.MyToolboxControl**. È possibile modificare questi nomi nel file *MyToolboxControl.xaml.cs.*

1. Aprire *MyToolboxControl.xaml.cs* nella vista codice.

2. Individuare `MyToolboxControl` la classe e rinominarla in TestControl. (Il modo più veloce per eseguire questa operazione consiste nel rinominare la classe, quindi **selezionare Rinomina** dal menu di scelta rapida e completare i passaggi. (Per ulteriori informazioni sul comando **Rinomina,** vedere [Rinominare il refactoring (C)](../ide/reference/rename.md).

3. Passare all'attributo `ProvideToolboxControl` e modificare il valore del primo parametro in **Test**. Si tratta del nome del gruppo che conterrà il controllo nella **casella degli strumenti**.

    Il codice risultante dovrebbe essere simile al seguente:The resulting code should look like this:

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

 Quando si esegue il debug del progetto, è necessario trovare il controllo installato nella **casella degli strumenti** dell'istanza sperimentale di Visual Studio.

### <a name="to-build-and-test-the-control"></a>Per compilare e testare il controllo

1. Ricompilare il progetto e avviare il debug.

2. Nella nuova istanza di Visual Studio creare un progetto di applicazione WPF. Assicurarsi che la finestra di progettazione XAML sia aperta.

3. Individuare il controllo nella **casella degli strumenti** e trascinarlo nell'area di progettazione.

4. Avviare il debug dell'applicazione WPF.

5. Verificare che venga visualizzato il controllo.

### <a name="to-deploy-the-control"></a>Per distribuire il controllo

1. Dopo aver compilato il progetto testato, è possibile trovare il file\* Con estensione *vsix* nella cartella .bin.debug del progetto.

2. È possibile installarlo in un computer locale facendo doppio clic sul file *VSIX* e seguendo la procedura di installazione. Per disinstallare il controllo, passare a**Estensioni e aggiornamenti** degli **strumenti** > e cercare l'estensione del controllo, quindi fare clic su **Disinstalla**.

3. Caricare il file *VSIX* in una rete o in un sito Web.

    Se si carica il file nel sito Web di [Visual Studio Marketplace,](https://marketplace.visualstudio.com/) altri utenti possono **utilizzare** > **le estensioni e gli aggiornamenti** degli strumenti in Visual Studio per trovare il controllo online e installarlo.
