---
title: Creazione di una pagina iniziale personalizzata Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739636"
---
# <a name="creating-a-custom-start-page"></a>Creazione di una pagina iniziale personalizzata

È possibile creare una pagina iniziale personalizzata seguendo la procedura descritta in questo documento.

## <a name="create-a-blank-start-page"></a>Creare una pagina iniziale vuota

In primo luogo, creare una pagina iniziale vuota creando un file con estensione xaml con una struttura di tag che verrà riconosciuta da Visual Studio.First, make a blank Start Page by creating a *.xaml* file that has a tag structure that Visual Studio will recognize. Aggiungere quindi markup e code-behind per produrre l'aspetto e la funzionalità desiderati.

1. Creare un nuovo progetto del tipo **Applicazione WPF** **(Desktop** > **di Windows**di Visual C

2. Aggiungere un riferimento a `Microsoft.VisualStudio.Shell.14.0`.

3. Aprire il file XAML nell'editor XML \<e modificare l'elemento Window> di primo livello in un \<elemento> UserControl senza rimuovere le dichiarazioni dello spazio dei nomi.

4. Rimuovere `x:Class` la dichiarazione dall'elemento di primo livello. In questo modo il contenuto XAML è compatibile con la finestra degli strumenti di Visual Studio che ospita la pagina iniziale.

5. Aggiungere le seguenti dichiarazioni dello \<spazio dei nomi all'elemento UserControl> di primo livello.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Questi spazi dei nomi consentono di accedere ai comandi, ai controlli e alle impostazioni dell'interfaccia utente di Visual Studio.These namespaces let you access Visual Studio commands, controls, and UI settings. Per ulteriori informazioni, vedere Aggiungere comandi di [Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Nell'esempio seguente viene illustrato il markup nel file *XAML* per una pagina iniziale vuota. Qualsiasi contenuto personalizzato deve <xref:System.Windows.Controls.Grid> essere contenuto nell'elemento interno.

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

6. Aggiungere controlli all'elemento \<vuoto UserControl> per compilare la pagina iniziale personalizzata. Per informazioni su come aggiungere funzionalità specifiche di Visual Studio, vedere Aggiungere comandi di [Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Testare e applicare la pagina iniziale personalizzata

Non impostare l'istanza principale di Visual Studio per eseguire la pagina iniziale personalizzata fino a quando non si verifica che non si verifichi l'arresto anomalo di Visual Studio. Al contrario, testarlo nell'istanza sperimentale.

### <a name="to-test-a-manually-created-custom-start-page"></a>Per testare una pagina iniziale personalizzata creata manualmenteTo test a manually-created custom Start Page

1. Copiare il file XAML e tutti i file di testo o di markup di supporto nella cartella *%USERPROFILE%.\\ *

2. Se la pagina iniziale fa riferimento a controlli o tipi in assembly che non sono installati da Visual Studio, copiare gli assembly e quindi incollarli nella *cartella\\*di installazione di Visual Studio.

3. Al prompt dei comandi di Visual Studio digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.

4. Nell'istanza sperimentale, **vai alla** > pagina Strumenti**Opzioni** > di**avvio** dell'ambiente**Environment** > e seleziona il file XAML dall'elenco a discesa Personalizza **pagina iniziale.**

5. Scegliere **Pagina iniziale** dal menu **Visualizza**.

     Verrà visualizzata la pagina iniziale personalizzata. Se si desidera modificare i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi riaprire l'istanza sperimentale per visualizzare le modifiche.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Per applicare la pagina iniziale personalizzata nell'istanza primaria di Visual StudioTo apply the custom start page in the primary instance of Visual Studio

- Dopo aver testato la pagina iniziale e averla trovata stabile, utilizzare l'opzione **Personalizza pagina iniziale** nella finestra di dialogo **Opzioni** per selezionarla come pagina iniziale nell'istanza primaria di Visual Studio

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Aggiungere codice XAML personalizzato alla pagina inizialeWalkthrough: Add custom XAML to the Start Page](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Aggiungere il controllo utente alla pagina inizialeAdd user control to the Start Page](../extensibility/adding-user-control-to-the-start-page.md)
- [Aggiungere comandi di Visual Studio a una pagina inizialeAdd Visual Studio commands to a Start Page](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Procedura dettagliata: Salvare le impostazioni utente in una pagina inizialeWalkthrough: Save user settings on a Start Page](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Distribuire pagine iniziali personalizzateDeploy custom Start Pages](../extensibility/deploying-custom-start-pages.md)
