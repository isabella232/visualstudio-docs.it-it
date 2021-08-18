---
title: Aggiunta Visual Studio comandi a una pagina iniziale | Microsoft Docs
description: Informazioni sui diversi modi per associare Visual Studio comandi a oggetti XAML in una pagina iniziale personalizzata in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 9d63d7267002577f72a03980eceed0b857e13157
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051352"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Aggiungere Visual Studio comandi a una pagina iniziale

Quando si crea una pagina iniziale personalizzata, è possibile aggiungervi Visual Studio comandi personalizzati. Questo documento illustra i diversi modi per associare Visual Studio comandi xaml agli oggetti XAML in una pagina iniziale.

Per altre informazioni sui comandi in XAML, vedere [Panoramica dei comandi](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Aggiungere comandi dall'elenco comandi

Nella pagina iniziale creata in [Creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) sono stati aggiunti gli spazi dei nomi e , come indicato di <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> seguito.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Aggiungere un altro spazio dei nomi per Microsoft.VisualStudio.Shell dall'assembly *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. Potrebbe essere necessario aggiungere un riferimento a questo assembly nel progetto.

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

È possibile usare l'alias per associare Visual Studio comandi ai controlli XAML nella pagina impostando la proprietà `vscom:` <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> del controllo su `vscom:VSCommands.ExecuteCommand` . È quindi possibile impostare <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> la proprietà sul nome del comando da eseguire, come illustrato nell'esempio seguente.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> `x:`L'alias, che fa riferimento allo schema XAML, è obbligatorio all'inizio di tutti i comandi.

 È possibile impostare il valore della proprietà su qualsiasi comando accessibile `Command` dalla **finestra di** comando. Per un elenco dei comandi disponibili, vedere Visual Studio [alias dei comandi](../ide/reference/visual-studio-command-aliases.md).

 Se il comando da aggiungere richiede un parametro aggiuntivo, è possibile aggiungerlo al valore della `CommandParameter` proprietà . Separare i parametri dai comandi usando spazi, come illustrato nell'esempio seguente.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Chiamare le estensioni dall'well del comando
 È possibile chiamare comandi da VSPackage registrati usando la stessa sintassi usata per chiamare altri Visual Studio comandi. Ad esempio, se un VSPackage installato aggiunge un **comando Home Page** al menu **Visualizza,** è possibile chiamare tale comando impostando `CommandParameter` su `View.HomePage` .

> [!NOTE]
> Se si chiama un comando associato a un VSPackage, il pacchetto deve essere caricato quando viene richiamato il comando.

## <a name="add-commands-from-assemblies"></a>Aggiungere comandi da assembly
 Per chiamare un comando da un assembly o per accedere al codice in un VSPackage non associato a un comando di menu, è necessario creare un alias per l'assembly e quindi chiamare l'alias.

### <a name="to-call-a-command-from-an-assembly"></a>Per chiamare un comando da un assembly

1. Nella soluzione aggiungere un riferimento all'assembly.

2. Nella parte superiore del file *StartPage.xaml* aggiungere una direttiva namespace per l'assembly, come illustrato nell'esempio seguente.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Richiamare il comando impostando la `Command` proprietà di un oggetto XAML, come illustrato nell'esempio seguente.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> È necessario copiare l'assembly e incollarlo in *.. \\ {Visual Studio cartella di installazione}\Common7\IDE\PrivateAssemblies per assicurarsi che venga \* caricato prima della chiamata.

## <a name="add-commands-with-the-dte-object"></a>Aggiungere comandi con l'oggetto DTE
 È possibile accedere all'oggetto DTE da una pagina iniziale, sia nel markup che nel codice.

 Nel markup è possibile accedervi usando la sintassi [dell'estensione di markup](/dotnet/framework/wpf/advanced/binding-markup-extension) di associazione per chiamare l'oggetto <xref:EnvDTE.DTE> . È possibile usare questo approccio per eseguire l'associazione a proprietà semplici, ad esempio quelle che restituiscono raccolte, ma non a metodi o servizi. Nell'esempio seguente viene illustrato un controllo associato alla proprietà e un controllo che enumera le proprietà dell'insieme <xref:System.Windows.Controls.TextBlock> <xref:EnvDTE._DTE.Name%2A> <xref:System.Windows.Controls.ListBox> <xref:EnvDTE.Window.Caption%2A> restituito dalla <xref:EnvDTE._DTE.Windows%2A> proprietà .

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

 Per un esempio, vedere [Procedura dettagliata: salvataggio delle impostazioni utente in una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Vedi anche

- [Aggiunta del controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
