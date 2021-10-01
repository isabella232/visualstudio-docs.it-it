---
title: Usare i dati della fase di progettazione con finestra di progettazione XAML in Visual Studio
description: Informazioni su come usare i dati in fase di progettazione in XAML.
ms.date: 09/30/2021
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
monikerRange: '>=vs-2019'
ms.openlocfilehash: 83846eb0e37adb925c09cf31ebb46c8a50e2d143
ms.sourcegitcommit: 65a1b6aae8387735f05a83b45e1a6865e9805e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2021
ms.locfileid: "129339912"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Usare i dati della fase di progettazione con finestra di progettazione XAML in Visual Studio

Alcuni layout sono difficili da visualizzare senza dati. In questo documento verrà esaminato uno degli approcci che gli sviluppatori che lavorano ai progetti desktop possono usare per schernire i dati nella finestra di progettazione XAML. Questo approccio viene eseguito usando lo spazio dei nomi "d:" ignorabile esistente. Con questo approccio è possibile aggiungere rapidamente dati in fase di progettazione alle pagine o ai controlli senza la necessità di creare un ViewModel fittizio completo o semplicemente testare come una modifica di proprietà potrebbe influire sull'applicazione senza preoccuparsi che queste modifiche influiranno sulle build di versione. All d: i dati vengono usati solo dal finestra di progettazione XAML e nell'applicazione non vengono compilati valori dello spazio dei nomi ignorabili.

> [!NOTE]
> se si usa Xamarin.Forms, vedere [Xamarin.Forms Design Time Data](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Nozioni di base sui dati della fase di progettazione

I dati in fase di progettazione sono dati fittizi impostati per semplificare la visualizzazione dei controlli finestra di progettazione XAML. Per iniziare, aggiungere le righe di codice seguenti all'intestazione del documento XAML, se non sono già presenti:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Dopo aver aggiunto gli spazi dei nomi, è possibile inserire qualsiasi attributo o controllo per mostrarlo solo nel finestra di progettazione XAML `d:` ma non in fase di esecuzione.

Ad esempio, è possibile aggiungere testo a un oggetto TextBlock a cui in genere sono associati dati.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Dati in fase di progettazione con testo in un controllo TextBlock](media\xaml-design-time-textblock.png "Dati in fase di progettazione con testo un'etichetta")](media\xaml-design-time-textblock.png#lightbox)

In questo esempio, senza `d:Text` , il finestra di progettazione XAML non mostrerebbe nulla per TextBlock. Viene invece visualizzato "Name!" in cui TextBlock avrà dati reali in fase di esecuzione.

È possibile usare con attributi per qualsiasi controllo UWP o WPF .NET Core, ad esempio `d:` colori, dimensioni dei caratteri e spaziatura. È anche possibile aggiungerlo al controllo stesso.

```xml
<d:Button Content="Design Time Button" />
```

[![Dati in fase di progettazione con un controllo Button](media\xaml-design-time-button.png "Dati in fase di progettazione con un controllo Button")](media\xaml-design-time-button.png#lightbox)

In questo esempio il pulsante viene visualizzato solo in fase di progettazione. Usare questo metodo per inserire un segnaposto in per un controllo personalizzato o per provare controlli diversi. Tutti `d:` gli attributi e i controlli verranno ignorati durante il runtime.

## <a name="preview-images-at-design-time"></a>Anteprima delle immagini in fase di progettazione

È possibile impostare un'origine in fase di progettazione per le immagini associate alla pagina o caricate in modo dinamico. Aggiungere l'immagine che si vuole visualizzare nel finestra di progettazione XAML al progetto. È quindi possibile visualizzare l'immagine nel finestra di progettazione XAML in fase di progettazione:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> L'immagine in questo esempio deve esistere nella soluzione.

## <a name="design-time-data-for-listviews"></a>Dati in fase di progettazione per ListView

ListViews è un modo comune per visualizzare i dati nell'app Desktop. Tuttavia, sono difficili da visualizzare senza dati. È possibile usare questa funzionalità per creare dati inline della fase di progettazione ItemSource o Items. Il finestra di progettazione XAML visualizza gli elementi della matrice in ListView in fase di progettazione.

### <a name="wpf-net-core-example"></a>Esempio di WPF .NET Core
Per usare il tipo system:String, assicurarsi di includere `xmlns:system="clr-namespace:System;assembly=mscorlib` nell'intestazione XAML.

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![Dati in fase di progettazione con un controllo ListView](media\xaml-design-time-listview-strings.png "Dati in fase di progettazione con un controllo ListView")](media\xaml-design-time-listview-strings.png#lightbox)

Questo esempio precedente mostra un controllo ListView con tre TextBlock nell'finestra di progettazione XAML.

È anche possibile creare una matrice di oggetti dati. Ad esempio, le proprietà pubbliche di un `City` oggetto dati possono essere costruite come dati in fase di progettazione.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

Per usare la classe in XAML, è necessario importare lo spazio dei nomi nel nodo radice.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![Modello effettivo nei dati in fase di progettazione con un controllo ListView](media\xaml-design-time-listview-models.png "Dati effettivi della fase di progettazione del modello con un controllo ListView")](media\xaml-design-time-listview-models.png#lightbox)

Il vantaggio è che è possibile associare i controlli a una versione statica in fase di progettazione del modello.

### <a name="uwp-example"></a>Esempio UWP

x:Array non è supportato nella UWP. È quindi possibile `<d:ListView.Items>` usare . Per usare il tipo system:String, assicurarsi di includere `http://schemas.microsoft.com/winfx/2009/xaml` nell'intestazione XAML.

```xml
    <StackPanel>
        <ListView>
            <d:ListView.Items>
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </d:ListView.Items>
        </ListView>
    </StackPanel>
```

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Usare dati in fase di progettazione con proprietà e tipi personalizzati

Questa funzionalità per impostazione predefinita funziona solo con i controlli e le proprietà della piattaforma. In questa sezione vengono descritti i passaggi necessari per consentire l'uso di controlli personalizzati come controlli in fase di progettazione, una nuova funzionalità disponibile per i clienti che usano Visual Studio 2019 [versione 16.8](/visualstudio/releases/2019/release-notes/) o successiva. Esistono tre requisiti per abilitare questa funzionalità:

- Spazio dei nomi xmlns personalizzato

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Versione in fase di progettazione dello spazio dei nomi. A tale scopo, è sufficiente aggiungere /design alla fine.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Aggiunta del prefisso della fase di progettazione a mc:Ignorable

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Dopo aver effettuato tutti questi passaggi, è possibile usare il `myDesignTimeControls` prefisso per creare i controlli in fase di progettazione.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Creazione di uno spazio dei nomi xmlns personalizzato

Per creare uno spazio dei nomi xmlns personalizzato in WPF .NET Core, è necessario eseguire il mapping dello spazio dei nomi XML personalizzato allo spazio dei nomi CLR in cui si sono contenuti i controlli. A tale scopo, aggiungere `XmlnsDefinition` l'attributo a livello di assembly nel `AssemblyInfo.cs` file. Il file si trova nella gerarchia radice del progetto.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verifica un problema non elencato in questa sezione, segnalarci il problema usando lo [strumento Segnala un](../ide/how-to-report-a-problem-with-visual-studio.md) problema.

### <a name="requirements"></a>Requisiti

- I dati in fase di progettazione Visual Studio 2019 [versione 16.7](/visualstudio/releases/2019/release-notes-v16.7) o successiva.

- Supporta Windows desktop che hanno come destinazione Windows Presentation Foundation (WPF) per .NET Core e UWP. Questa funzionalità è disponibile anche per .NET Framework nel [canale di anteprima](/visualstudio/releases/2019/release-notes-preview). Per abilitarlo, passare **a** Strumenti Opzioni Funzionalità di anteprima dell'ambiente, selezionare New WPF finestra di progettazione XAML for  >    >    >   **.NET Framework** e quindi riavviare Visual Studio.

- A partire Visual Studio 2019 versione 16.7, questa funzionalità funziona con tutti i controlli in-the-box dei framework WPF e UWP. Il supporto per i controlli di terze parti è ora disponibile nella [versione 16.8.](/visualstudio/releases/2019/release-notes/)

### <a name="the-xaml-designer-stopped-working"></a>Il finestra di progettazione XAML ha smesso di funzionare

Provare a chiudere e riaprire il file XAML e a pulire e ricompilare il progetto.

## <a name="see-also"></a>Vedi anche

- [Dati in fase di progettazione con L'anteprima di Xamarin.Forms](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [XAML in all WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)