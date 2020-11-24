---
title: Aggiunta di comandi di Visual Studio a una pagina iniziale | Microsoft Docs
description: Informazioni sui diversi modi per associare i comandi di Visual Studio agli oggetti XAML in una pagina iniziale personalizzata in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 7784b077093660eb5f9c9a0bf471a8965811ba72
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597522"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Aggiungere i comandi di Visual Studio a una pagina iniziale

Quando si crea una pagina iniziale personalizzata, è possibile aggiungervi i comandi di Visual Studio. In questo documento vengono illustrati i diversi modi per associare i comandi di Visual Studio agli oggetti XAML in una pagina iniziale.

Per ulteriori informazioni sui comandi in XAML, vedere [Cenni preliminari sul comando](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Aggiungere i comandi dal pozzetto dei comandi

La pagina iniziale creata in [creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) ha aggiunto <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> gli <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> spazi dei nomi e, come indicato di seguito.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Aggiungere un altro spazio dei nomi per Microsoft. VisualStudio. Shell dall'assembly *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. Potrebbe essere necessario aggiungere un riferimento a questo assembly nel progetto.

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

È possibile usare l' `vscom:` alias per associare i comandi di Visual Studio ai controlli XAML nella pagina impostando la <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> proprietà del controllo su `vscom:VSCommands.ExecuteCommand` . È quindi possibile impostare la <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> proprietà sul nome del comando da eseguire, come illustrato nell'esempio seguente.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> L' `x:` alias, che fa riferimento allo schema XAML, è necessario all'inizio di tutti i comandi.

 È possibile impostare il valore della `Command` proprietà su qualsiasi comando a cui è possibile accedere dalla finestra di **comando** . Per un elenco di comandi disponibili, vedere alias dei comandi di [Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Se il comando da aggiungere richiede un parametro aggiuntivo, è possibile aggiungerlo al valore della `CommandParameter` Proprietà. Separare i parametri dai comandi usando spazi, come illustrato nell'esempio seguente.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Chiamare le estensioni dal pozzetto dei comandi
 È possibile chiamare i comandi da VSPackage registrati usando la stessa sintassi usata per chiamare altri comandi di Visual Studio. Se, ad esempio, un pacchetto VSPackage installato aggiunge un comando della **Home page** al menu **Visualizza** , è possibile chiamare il comando impostando `CommandParameter` su `View.HomePage` .

> [!NOTE]
> Se si chiama un comando associato a un VSPackage, il pacchetto deve essere caricato quando viene richiamato il comando.

## <a name="add-commands-from-assemblies"></a>Aggiungere comandi da assembly
 Per chiamare un comando da un assembly o per accedere al codice in un VSPackage non associato a un comando di menu, è necessario creare un alias per l'assembly e quindi chiamare l'alias.

### <a name="to-call-a-command-from-an-assembly"></a>Per chiamare un comando da un assembly

1. Nella soluzione aggiungere un riferimento all'assembly.

2. Nella parte superiore del file *StartPage. XAML* aggiungere una direttiva Namespace per l'assembly, come illustrato nell'esempio seguente.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Richiamare il comando impostando la `Command` proprietà di un oggetto XAML, come illustrato nell'esempio seguente.

     XAML

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> È necessario copiare l'assembly e incollarlo in *.. \\ {Cartella di installazione di Visual Studio} \Common7\IDE\PrivateAssemblies \* per assicurarsi che venga caricata prima di essere chiamata.

## <a name="add-commands-with-the-dte-object"></a>Aggiungere comandi con l'oggetto DTE
 È possibile accedere all'oggetto DTE da una pagina iniziale, sia nel markup che nel codice.

 Nel markup, è possibile accedervi usando la sintassi dell' [estensione di markup dell'associazione](/dotnet/framework/wpf/advanced/binding-markup-extension) per chiamare l' <xref:EnvDTE.DTE> oggetto. È possibile utilizzare questo approccio per eseguire il binding a proprietà semplici, ad esempio quelle che restituiscono raccolte, ma non è possibile eseguire l'associazione a metodi o servizi. Nell'esempio seguente viene illustrato un <xref:System.Windows.Controls.TextBlock> controllo associato alla <xref:EnvDTE._DTE.Name%2A> proprietà e un <xref:System.Windows.Controls.ListBox> controllo che enumera le <xref:EnvDTE.Window.Caption%2A> proprietà della raccolta restituita dalla <xref:EnvDTE._DTE.Windows%2A> Proprietà.

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

 Per un esempio, vedere [procedura dettagliata: salvataggio delle impostazioni utente in una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Vedere anche

- [Aggiunta del controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
