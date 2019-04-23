---
title: Pagina iniziale di creazione di un oggetto personalizzato | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4fc12744dbf979a338cbc551a715284dffdf7385
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090130"
---
# <a name="creating-a-custom-start-page"></a>Creazione di una pagina iniziale personalizzata

È possibile creare una pagina iniziale personalizzata seguendo i passaggi descritti in questo documento.

## <a name="create-a-blank-start-page"></a>Creare una pagina iniziale vuota

Assicurarsi prima di tutto una pagina iniziale vuota creando un *XAML* file che ha una struttura di tag che verranno riconosciute dallo Visual Studio. Aggiungere quindi il markup e code-behind per produrre l'aspetto e funzionalità che si desidera.

1. Creare un nuovo progetto di tipo **applicazione WPF** (**Visual c#** > **Windows Desktop**).

2. Aggiungere un riferimento a `Microsoft.VisualStudio.Shell.14.0`.

3. Aprire il file XAML nell'editor XML e cambiare il livello superiore \<finestra > elemento da un \<UserControl > elemento senza rimuovere una delle dichiarazioni dello spazio dei nomi.

4. Rimuovere il `x:Class` dichiarazione di elemento di primo livello. In questo modo il contenuto XAML compatibile con la finestra degli strumenti di Visual Studio che ospita la pagina iniziale.

5. Aggiungere le seguenti dichiarazioni dello spazio dei nomi di livello principale \<UserControl > elemento.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Questi spazi dei nomi consentono di accedere ai comandi di Visual Studio, controlli e le impostazioni dell'interfaccia utente. Per altre informazioni, vedere [comandi di Visual Studio aggiungere a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Nell'esempio seguente viene illustrato il markup nel *XAML* file per una pagina iniziale vuota. Qualsiasi contenuto personalizzato devono essere inseriti in interna <xref:System.Windows.Controls.Grid> elemento.

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

6. Aggiungere controlli a vuoto \<UserControl > elemento per riempire la pagina iniziale personalizzata. Per informazioni su come aggiungere funzionalità specifiche per Visual Studio, vedere [comandi di Visual Studio aggiungere a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Test e applicare la pagina iniziale personalizzata

Non impostare l'istanza primaria di Visual Studio per l'esecuzione della pagina iniziale personalizzata fino a quando non si verifica che causa l'arresto anomalo Visual Studio. Al contrario, testarla nell'istanza sperimentale.

### <a name="to-test-a-manually-created-custom-start-page"></a>Per testare una creati manualmente pagina iniziale di personalizzata

1. Copiare il file XAML e qualsiasi file di testo o markup supporto file, per il *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\*  cartella.

2. Se la pagina iniziale di fa riferimento a tutti i controlli o i tipi negli assembly che non sono installati da Visual Studio, copiare gli assembly e quindi incollarli nella *\Common7\IDE\PrivateAssemblies. {cartella di installazione di Visual Studio}\\* .

3. Un prompt dei comandi di Visual Studio, digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.

4. Nell'istanza sperimentale, passare al **degli strumenti** > **opzioni** > **ambiente** > **avvio** pagina e selezionare il file XAML dal **Personalizza pagina iniziale** elenco a discesa.

5. Scegliere **Pagina iniziale** dal menu **Visualizza**.

     La pagina iniziale personalizzata deve essere visualizzata. Se si desidera modificare tutti i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi aprire nuovamente l'istanza sperimentale per visualizzare le modifiche.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Per applicare la pagina personalizzata iniziale nell'istanza primaria di Visual Studio

- Dopo avere testato la pagina iniziale e ha rilevato che è stabile, usare il **Personalizza pagina iniziale** opzione il **opzioni** finestra di dialogo per selezionarla come pagina iniziale nell'istanza primaria di Visual Studio

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Aggiungere XAML personalizzato nella pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Aggiungi controllo utente nella pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
- [Aggiungere comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Procedura dettagliata: Salvare le impostazioni utente in una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Distribuire le pagine iniziali personalizzate](../extensibility/deploying-custom-start-pages.md)