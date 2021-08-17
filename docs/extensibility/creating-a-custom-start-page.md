---
title: Creazione di una pagina iniziale personalizzata | Microsoft Docs
description: Informazioni su come creare una pagina iniziale personalizzata. Iniziare con una pagina iniziale vuota, aggiungere controlli all'elemento UserControl vuoto e quindi testare la pagina.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 34e8f64b0007231ef3c5208d7020d415d65e6d67
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073539"
---
# <a name="creating-a-custom-start-page"></a>Creazione di una pagina iniziale personalizzata

È possibile creare una pagina iniziale personalizzata seguendo la procedura descritta in questo documento.

## <a name="create-a-blank-start-page"></a>Creare una pagina iniziale vuota

Per prima cosa, creare una pagina iniziale vuota creando un file con estensione *xaml* con una struttura di tag Visual Studio riconoscerà. Aggiungere quindi markup e code-behind per produrre l'aspetto e la funzionalità desiderati.

1. Creare un nuovo progetto di tipo **Applicazione WPF** (**Visual C#**  >  **Windows Desktop**).

2. Aggiungere un riferimento a `Microsoft.VisualStudio.Shell.14.0`.

3. Aprire il file XAML nell'editor XML e modificare l'elemento di primo livello in un elemento senza rimuovere le \<Window> dichiarazioni dello spazio dei \<UserControl> nomi.

4. Rimuovere la `x:Class` dichiarazione dall'elemento di primo livello. In questo modo il contenuto XAML è compatibile con la Visual Studio degli strumenti che ospita la pagina iniziale.

5. Aggiungere le dichiarazioni dello spazio dei nomi seguenti all'elemento di primo \<UserControl> livello.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Questi spazi dei nomi consentono di accedere Visual Studio comandi, controlli e impostazioni dell'interfaccia utente. Per altre informazioni, vedere [Aggiungere Visual Studio comandi a una pagina iniziale.](../extensibility/adding-visual-studio-commands-to-a-start-page.md)

     L'esempio seguente mostra il markup nel file *con estensione xaml* per una pagina iniziale vuota. Qualsiasi contenuto personalizzato deve essere contenuto nell'elemento <xref:System.Windows.Controls.Grid> interno.

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

6. Aggiungere controlli \<UserControl> all'elemento vuoto per compilare la pagina iniziale personalizzata. Per informazioni su come aggiungere funzionalità specifiche per Visual Studio, vedere Aggiungere Visual Studio [comandi a una pagina iniziale.](../extensibility/adding-visual-studio-commands-to-a-start-page.md)

## <a name="test-and-apply-the-custom-start-page"></a>Testare e applicare la pagina iniziale personalizzata

Non impostare l'istanza primaria di Visual Studio per eseguire la pagina iniziale personalizzata fino a quando non si verifica che non si verifichi un arresto anomalo Visual Studio. Testarlo invece nell'istanza sperimentale.

### <a name="to-test-a-manually-created-custom-start-page"></a>Per testare una pagina iniziale personalizzata creata manualmente

1. Copiare il file XAML e tutti i file di testo o di markup di supporto nella cartella *%USERPROFILE%\Documenti\Visual Studio 2015\StartPages. \\*

2. Se la pagina iniziale fa riferimento a controlli o tipi negli assembly non installati da Visual Studio, copiare gli assembly e incollarli nella cartella di installazione *{Visual Studio}\Common7\IDE\PrivateAssemblies \\*.

3. Al prompt Visual Studio comando digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.

4. Nell'istanza sperimentale passare alla pagina **Avvio** ambiente opzioni strumenti  >    >    >   e selezionare il file XAML nell'elenco a discesa **Personalizza pagina iniziale.**

5. Scegliere **Pagina iniziale** dal menu **Visualizza**.

     Verrà visualizzata la pagina iniziale personalizzata. Per modificare i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi ria aprire l'istanza sperimentale per visualizzare le modifiche.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Per applicare la pagina iniziale personalizzata nell'istanza primaria di Visual Studio

- Dopo aver testato la pagina iniziale e aver trovato  che fosse stabile, usare l'opzione Personalizza pagina iniziale nella finestra di dialogo Opzioni per selezionarla come pagina iniziale nell'istanza primaria di Visual Studio 

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Aggiungere codice XAML personalizzato alla pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Aggiungere il controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
- [Aggiungere Visual Studio comandi a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Procedura dettagliata: Salvare le impostazioni utente in una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Distribuire pagine iniziale personalizzate](../extensibility/deploying-custom-start-pages.md)
