---
title: Aggiunta di comandi di Visual Studio a una pagina iniziale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8461fdd3fd0aaedbbdd770a4e2762c4912c3ce0d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040159"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Aggiungere comandi di Visual Studio a una pagina iniziale

Quando si crea una pagina iniziale personalizzata, è possibile aggiungervi comandi di Visual Studio. Questo documento illustra i diversi modi per eseguire l'associazione di comandi di Visual Studio per gli oggetti XAML in una pagina iniziale.

Per altre informazioni sui comandi in XAML, vedere [Commanding Panoramica](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Aggiungere anche i comandi dal comando

Nella pagina iniziale creato in [creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) aggiunte le <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> e <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> spazi dei nomi, come indicato di seguito.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Aggiungere un altro spazio dei nomi per Microsoft.VisualStudio.Shell dall'assembly *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Si potrebbe essere necessario aggiungere un riferimento a questo assembly nel progetto.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

È possibile usare la `vscom:` controlla l'alias per associare i comandi di Visual Studio da XAML nella pagina impostando la <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> proprietà del controllo da `vscom:VSCommands.ExecuteCommand`. È quindi possibile impostare il <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> proprietà sul nome del comando da eseguire, come illustrato nell'esempio seguente.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
>  Il `x:` alias che fa riferimento allo schema XAML, è necessario all'inizio di tutti i comandi.

 È possibile impostare il valore della `Command` proprietà per tutti i comandi che è possibile accedere dal **comando** finestra. Per un elenco di comandi disponibili, vedere [alias di comandi di Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Se il comando per aggiungere richiede un parametro aggiuntivo, è possibile aggiungere al valore della `CommandParameter` proprietà. Parametri separati da comandi utilizzando spazi, come illustrato nell'esempio seguente.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Chiamare anche le estensioni del comando
 È possibile chiamare i comandi da pacchetti VSPackage registrati con la stessa sintassi che consente di chiamare gli altri comandi di Visual Studio. Ad esempio, se un pacchetto VSPackage installati aggiunge un **Home Page** comando per il **vista** menu, è possibile chiamare tale comando impostando `CommandParameter` a `View.HomePage`.

> [!NOTE]
>  Se si chiama un comando che è associato a un pacchetto VSPackage, è necessario caricare il pacchetto quando viene richiamato il comando.

## <a name="add-commands-from-assemblies"></a>Aggiungere comandi dagli assembly
 Per chiamare un comando da un assembly o accedere al codice in un pacchetto VSPackage che non è associato a un comando di menu, è necessario creare un alias per l'assembly e quindi chiamare l'alias.

### <a name="to-call-a-command-from-an-assembly"></a>Per chiamare un comando da un assembly

1. Nella soluzione, aggiungere un riferimento all'assembly.

2. In cima il *StartPage* file, aggiungere una direttiva dello spazio dei nomi per l'assembly, come illustrato nell'esempio seguente.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Richiamare il comando impostando il `Command` proprietà di un oggetto XAML, come illustrato nell'esempio seguente.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
>  È necessario copiare l'assembly e quindi incollarlo in *... \\\Common7\IDE\PrivateAssemblies. {cartella di installazione di visual Studio}\* per assicurarsi che il caricamento prima che venga chiamato.

## <a name="add-commands-with-the-dte-object"></a>Aggiungere i comandi con l'oggetto DTE
 È possibile accedere all'oggetto DTE da una pagina iniziale, nel markup e nel codice.

 Nel markup, è possibile accedervi usando il [estensione di Markup Binding](/dotnet/framework/wpf/advanced/binding-markup-extension) sintassi per chiamare il <xref:EnvDTE.DTE> oggetto. È possibile usare questo approccio da associare alla proprietà semplici, ad esempio quelli che restituiscono raccolte, ma non è possibile associare ai metodi o servizi. L'esempio seguente mostra una <xref:System.Windows.Controls.TextBlock> controllo associato al <xref:EnvDTE._DTE.Name%2A> proprietà e un <xref:System.Windows.Controls.ListBox> controllo che enumera il <xref:EnvDTE.Window.Caption%2A> le proprietà della raccolta restituito dal <xref:EnvDTE._DTE.Windows%2A> proprietà.

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Per un esempio, vedere [Procedura dettagliata: Salvataggio delle impostazioni utente in una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Vedere anche

- [Aggiunta di controllo utente nella pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)