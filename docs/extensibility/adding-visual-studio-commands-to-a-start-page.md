---
title: Aggiunta di comandi di Visual Studio a una pagina iniziale Documenti Microsoft
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
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740122"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Aggiungere comandi di Visual Studio a una pagina inizialeAdd Visual Studio commands to a Start Page

Quando si crea una pagina iniziale personalizzata, è possibile aggiungervi comandi di Visual Studio.When you create a custom Start Page, you can add Visual Studio commands to it. Questo documento illustra i diversi modi per associare i comandi di Visual Studio agli oggetti XAML in una pagina iniziale.

Per altre informazioni sui comandi in XAML, vedere [Panoramica dei comandiFor more](/dotnet/framework/wpf/advanced/commanding-overview) information about commands in XAML, see Commanding overview

## <a name="add-commands-from-the-command-well"></a>Aggiungere comandi dal riquadro dei comandi

La pagina iniziale creata in Creare <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> una [pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) ha aggiunto gli spazi dei nomi e, come indicato di seguito.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Aggiungere un altro spazio dei nomi per Microsoft.VisualStudio.Shell dall'assembly *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. Potrebbe essere necessario aggiungere un riferimento a questo assembly nel progetto.

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

È possibile `vscom:` utilizzare l'alias per associare i comandi <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> di Visual Studio `vscom:VSCommands.ExecuteCommand`ai controlli XAML nella pagina impostando la proprietà del controllo su . È quindi possibile <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> impostare la proprietà sul nome del comando da eseguire, come illustrato nell'esempio seguente.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> L'alias, `x:` che fa riferimento allo schema XAML, è obbligatorio all'inizio di tutti i comandi.

 È possibile impostare `Command` il valore della proprietà su qualsiasi comando accessibile dalla finestra **di comando.** Per un elenco dei comandi disponibili, vedere Alias dei comandi di [Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Se il comando da aggiungere richiede un parametro aggiuntivo, `CommandParameter` è possibile aggiungerlo al valore della proprietà. Separare i parametri dai comandi utilizzando gli spazi, come illustrato nell'esempio seguente.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Chiamare le estensioni dal comando bene
 È possibile chiamare i comandi da VSPackage registrati utilizzando la stessa sintassi utilizzata per chiamare altri comandi di Visual Studio.You can call commands from registered VSPackages by using the same syntax that is used to call other Visual Studio commands. Ad esempio, se un VSPackage installato aggiunge un comando **Home Page** per `CommandParameter` `View.HomePage`il **Visualizza** menu, è possibile chiamare tale comando impostando su .

> [!NOTE]
> Se si chiama un comando associato a un VSPackage, il pacchetto deve essere caricato quando viene richiamato il comando.

## <a name="add-commands-from-assemblies"></a>Aggiungere comandi dagli assembly
 Per chiamare un comando da un assembly o per accedere al codice in un VSPackage che non è associato a un comando di menu, è necessario creare un alias per l'assembly e quindi chiamare l'alias.

### <a name="to-call-a-command-from-an-assembly"></a>Per chiamare un comando da un assemblyTo call a command from an assembly

1. Nella soluzione aggiungere un riferimento all'assembly.

2. All'inizio del file *StartPage.xaml* aggiungere una direttiva dello spazio dei nomi per l'assembly, come illustrato nell'esempio seguente.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Richiamare il comando `Command` impostando la proprietà di un oggetto XAML, come illustrato nell'esempio seguente.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> È necessario copiare l'assembly e quindi incollarlo in . \\Per assicurarsi che venga caricata prima della chiamata, è possibile che venga caricato prima della\* chiamata.

## <a name="add-commands-with-the-dte-object"></a>Aggiungere comandi con l'oggetto DTE
 È possibile accedere all'oggetto DTE da una pagina iniziale, sia nel markup che nel codice.

 Nel markup, è possibile accedervi utilizzando il Binding <xref:EnvDTE.DTE> Markup [Extension](/dotnet/framework/wpf/advanced/binding-markup-extension) sintassi per chiamare l'oggetto. È possibile usare questo approccio per eseguire l'associazione a proprietà semplici, ad esempio quelle che restituiscono raccolte, ma non è possibile eseguire l'associazione a metodi o servizi. Nell'esempio seguente <xref:System.Windows.Controls.TextBlock> viene illustrato un <xref:EnvDTE._DTE.Name%2A> controllo che <xref:System.Windows.Controls.ListBox> esegue l'associazione alla proprietà e un controllo che enumera le <xref:EnvDTE.Window.Caption%2A> proprietà della raccolta restituita dalla <xref:EnvDTE._DTE.Windows%2A> proprietà .

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

## <a name="see-also"></a>Vedere anche

- [Aggiunta del controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
