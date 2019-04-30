---
title: Aggiunta di comandi di Visual Studio a una pagina iniziale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 638c9c0f0d024830124445485dcf9991678bd4d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429004"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Aggiunta di comandi di Visual Studio in una pagina iniziale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si crea una pagina iniziale personalizzata, è possibile aggiungervi comandi di Visual Studio. Questo documento illustra i diversi modi per associare i comandi di Visual Studio per gli oggetti XAML in una pagina iniziale.  
  
 Per altre informazioni sui comandi in XAML, vedere [Cenni preliminari](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Aggiunta di comandi anche dal comando  
 La pagina di avvio creato in [creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) aggiunto il <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> e <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> spazi dei nomi, come indicato di seguito.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Aggiungere un altro spazio dei nomi per Microsoft.VisualStudio.Shell dall'assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Si potrebbe essere necessario aggiungere un riferimento a questo assembly nel progetto.)  
  
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
> Il `x:` alias che fa riferimento allo schema XAML, è necessario all'inizio di tutti i comandi.  
  
 È possibile impostare il valore della `Command` proprietà per tutti i comandi che è possibile accedere dal **comando** finestra. Per un elenco di comandi disponibili, vedere [Visual Studio Command Aliases](../ide/reference/visual-studio-command-aliases.md).  
  
 Se il comando per aggiungere richiede un parametro aggiuntivo, è possibile aggiungere al valore della `CommandParameter` proprietà. Parametri separati da comandi utilizzando spazi, come illustrato nell'esempio seguente.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Chiamata anche le estensioni del comando  
 È possibile chiamare i comandi da pacchetti VSPackage registrati con la stessa sintassi che consente di chiamare gli altri comandi di Visual Studio. Ad esempio, se un pacchetto VSPackage installati aggiunge un **Home Page** comando per il **vista** menu, è possibile chiamare tale comando impostando `CommandParameter` a `View.HomePage`.  
  
> [!NOTE]
> Se si chiama un comando che è associato a un pacchetto VSPackage, è necessario caricare il pacchetto quando viene richiamato il comando.  
  
## <a name="adding-commands-from-assemblies"></a>Aggiunta di comandi da assembly  
 Per chiamare un comando da un assembly o accedere al codice in un pacchetto VSPackage che non è associato a un comando di menu, è necessario creare un alias per l'assembly e quindi chiamare l'alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Per chiamare un comando da un assembly  
  
1. Nella soluzione, aggiungere un riferimento all'assembly.  
  
2. Nella parte superiore del file StartPage. XAML, aggiungere una direttiva dello spazio dei nomi per l'assembly, come illustrato nell'esempio seguente.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. Richiamare il comando impostando il `Command` proprietà di un oggetto XAML, come illustrato nell'esempio seguente.  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> È necessario copiare l'assembly e quindi incollarlo in... \\ *Cartella di installazione di visual Studio*\Common7\IDE\PrivateAssemblies\ per assicurarsi che il caricamento prima che venga chiamato.  
  
## <a name="adding-commands-with-the-dte-object"></a>Aggiunta di comandi con l'oggetto DTE  
 È possibile accedere all'oggetto DTE da una pagina iniziale, nel markup e nel codice.  
  
 Nel markup, è possibile accedervi usando il [estensione di Markup Binding](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) sintassi per chiamare il <xref:EnvDTE.DTE> oggetto. È possibile usare questo approccio da associare alla proprietà semplici, ad esempio quelli che restituiscono raccolte, ma non è possibile associare ai metodi o servizi. L'esempio seguente mostra una <xref:System.Windows.Controls.TextBlock> controllo associato al <xref:EnvDTE._DTE.Name%2A> proprietà e un <xref:System.Windows.Controls.ListBox> controllo che enumera il <xref:EnvDTE.Window.Caption%2A> le proprietà della raccolta restituito dal <xref:EnvDTE._DTE.Windows%2A> proprietà.  
  
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
  
 Per un esempio, vedere [Procedura dettagliata: Salvataggio delle impostazioni utente a una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di un controllo utente nella pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
