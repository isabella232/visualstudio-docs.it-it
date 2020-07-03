---
title: Creazione di una pagina iniziale personalizzata | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: ed35948158866b7d0bbb2e458c8f8bc2f7b3f844
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903677"
---
# <a name="creating-a-custom-start-page"></a>Creazione di una pagina iniziale personalizzata

È possibile creare una pagina iniziale personalizzata attenendosi alla procedura descritta in questo documento.

## <a name="create-a-blank-start-page"></a>Creare una pagina iniziale vuota

Per prima cosa, creare una pagina iniziale vuota creando un file con *estensione XAML* con una struttura di tag riconoscibile da Visual Studio. Aggiungere quindi il markup e il code-behind per produrre l'aspetto e le funzionalità desiderate.

1. Creare un nuovo progetto di tipo **applicazione WPF** (**Visual C#**  >  **Windows Desktop**).

2. Aggiungere un riferimento a `Microsoft.VisualStudio.Shell.14.0`.

3. Aprire il file XAML nell'editor XML e modificare l'elemento di primo livello in \<Window> un \<UserControl> elemento senza rimuovere le dichiarazioni dello spazio dei nomi.

4. Rimuovere la `x:Class` dichiarazione dall'elemento di primo livello. Questo rende il contenuto XAML compatibile con la finestra degli strumenti di Visual Studio che ospita la pagina iniziale.

5. Aggiungere le seguenti dichiarazioni dello spazio dei nomi all'elemento di livello principale \<UserControl> .

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Questi spazi dei nomi consentono di accedere ai comandi, ai controlli e alle impostazioni dell'interfaccia utente di Visual Studio. Per altre informazioni, vedere [aggiungere comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Nell'esempio seguente viene illustrato il markup nel file con *estensione XAML* per una pagina iniziale vuota. Qualsiasi contenuto personalizzato deve andare nell'elemento interno <xref:System.Windows.Controls.Grid> .

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. Aggiungere i controlli all' \<UserControl> elemento vuoto per compilare la pagina iniziale personalizzata. Per informazioni su come aggiungere funzionalità specifiche di Visual Studio, vedere [aggiungere comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Testare e applicare la pagina iniziale personalizzata

Non impostare l'istanza primaria di Visual Studio in modo che esegua la pagina iniziale personalizzata fino a quando non si verifica l'arresto anomalo di Visual Studio. In alternativa, eseguirne il test nell'istanza sperimentale.

### <a name="to-test-a-manually-created-custom-start-page"></a>Per testare una pagina iniziale personalizzata creata manualmente

1. Copiare il file XAML e tutti i file di testo o i file di markup di supporto nella cartella *%USERPROFILE%\My Documenti\Visual Studio 2015 \\ \ StartPages* .

2. Se la pagina iniziale fa riferimento a tutti i controlli o tipi negli assembly che non sono installati da Visual Studio, copiare gli assembly e quindi incollarli in *{cartella di installazione \\ di Visual Studio} \Common7\IDE\PrivateAssemblies*.

3. Al prompt dei comandi di Visual Studio digitare **devenv/rootsuffix exp** per aprire un'istanza sperimentale di Visual Studio.

4. Nell'istanza sperimentale, passare alla **Tools**  >  pagina di avvio dell'ambiente strumenti**Opzioni**  >  **Environment**  >  **Startup** e selezionare il file XAML dall'elenco a discesa **Personalizza pagina iniziale** .

5. Scegliere **Pagina iniziale** dal menu **Visualizza**.

     Verrà visualizzata la pagina iniziale personalizzata. Se si desidera modificare i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi riaprire l'istanza sperimentale per visualizzare le modifiche.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Per applicare la pagina iniziale personalizzata nell'istanza primaria di Visual Studio

- Dopo aver testato la pagina iniziale e averla trovata stabile, utilizzare l'opzione **Personalizza pagina iniziale** nella finestra di dialogo **Opzioni** per selezionarla come pagina iniziale nell'istanza primaria di Visual Studio.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: aggiungere XAML personalizzato alla pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Aggiungere il controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
- [Aggiungere i comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Procedura dettagliata: salvare le impostazioni utente in una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Distribuire pagine iniziali personalizzate](../extensibility/deploying-custom-start-pages.md)
