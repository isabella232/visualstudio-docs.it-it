---
title: Usare i dati della fase di progettazione con il finestra di progettazione XAML in Visual Studio
description: Informazioni su come usare i dati in fase di progettazione in XAML.
ms.date: 11/10/2020
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 1dd0b4df440f6addd474ef08e7bf0b2958a58076
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492895"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Usare i dati della fase di progettazione con il finestra di progettazione XAML in Visual Studio

Alcuni layout sono difficili da visualizzare senza dati. In questo documento verrà esaminato uno degli approcci che gli sviluppatori che lavorano sui progetti desktop possono usare per simulare i dati nella finestra di progettazione XAML. Questo approccio viene eseguito utilizzando lo spazio dei nomi "d:" ignorabile esistente. Con questo approccio è possibile aggiungere rapidamente dati della fase di progettazione alle pagine o ai controlli senza la necessità di creare un ViewModel di simulazione completo oppure solo testare il modo in cui una modifica di proprietà potrebbe influire sull'applicazione senza preoccuparsi che queste modifiche avranno effetto sulle compilazioni di rilascio. Tutti d: i dati vengono usati solo dal finestra di progettazione XAML e nessun valore dello spazio dei nomi ignorabile viene compilato nell'applicazione.

> [!NOTE]
> Se si usa Novell. Forms, vedere [dati della fase di progettazione di Novell. Forms](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Nozioni fondamentali sui dati in fase di progettazione

I dati della fase di progettazione sono dati fittizi impostati per semplificare la visualizzazione dei controlli nella finestra di progettazione XAML. Per iniziare, aggiungere le righe di codice seguenti all'intestazione del documento XAML se non sono già presenti:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Dopo aver aggiunto gli spazi dei nomi, è possibile posizionarli `d:` davanti a qualsiasi attributo o controllo per visualizzarli solo nell'finestra di progettazione XAML ma non in fase di esecuzione.

Ad esempio, è possibile aggiungere testo a un TextBlock che in genere contiene dati associati.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Dati della fase di progettazione con testo in un TextBlock](media\xaml-design-time-textblock.png "Dati della fase di progettazione con un'etichetta di testo")](media\xaml-design-time-textblock.png#lightbox)

In questo esempio, senza `d:Text` , il finestra di progettazione XAML non visualizzerà nulla per il TextBlock. Viene invece visualizzato "nome!" in cui TextBlock avrà dati reali in fase di esecuzione.

È possibile usare `d:` con gli attributi per qualsiasi controllo UWP o WPF di .NET Core, ad esempio i colori, le dimensioni del carattere e la spaziatura. È anche possibile aggiungerlo al controllo stesso.

```xml
<d:Button Content="Design Time Button" />
```

[![Dati della fase di progettazione con un controllo Button](media\xaml-design-time-button.png "Dati della fase di progettazione con un controllo Button")](media\xaml-design-time-button.png#lightbox)

In questo esempio, il pulsante viene visualizzato solo in fase di progettazione. Utilizzare questo metodo per inserire un segnaposto in per un controllo personalizzato o per provare controlli diversi. Tutti `d:` gli attributi e i controlli verranno ignorati durante il Runtime.

## <a name="preview-images-at-design-time"></a>Anteprima immagini in fase di progettazione

È possibile impostare un'origine della fase di progettazione per le immagini associate alla pagina o caricate in modo dinamico. Aggiungere l'immagine che si desidera visualizzare nel finestra di progettazione XAML al progetto. È quindi possibile visualizzare l'immagine nel finestra di progettazione XAML in fase di progettazione:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> L'immagine in questo esempio deve essere presente nella soluzione.

## <a name="design-time-data-for-listviews"></a>Dati della fase di progettazione per ListView

I ListView sono un modo comune per visualizzare i dati nell'app desktop. Tuttavia, sono difficili da visualizzare senza dati. È possibile usare questa funzionalità per creare un ItemSource di dati in fase di progettazione inline. Il finestra di progettazione XAML Visualizza il risultato della matrice in fase di progettazione nel controllo ListView. Questo è un esempio per WPF .NET Core. Per usare il tipo System: String, assicurarsi `xmlns:system="clr-namespace:System;assembly=mscorlib` di includere nell'intestazione XAML.

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

[![Dati della fase di progettazione con ListView](media\xaml-design-time-listview-strings.png "Dati della fase di progettazione con ListView")](media\xaml-design-time-listview-strings.png#lightbox)

Nell'esempio precedente viene illustrato un ListView con tre TextBlock nell'finestra di progettazione XAML.

È inoltre possibile creare una matrice di oggetti dati. Ad esempio, le proprietà pubbliche di un `City` oggetto dati possono essere costruite come dati della fase di progettazione.

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

[![Modello effettivo nei dati della fase di progettazione con ListView](media\xaml-design-time-listview-models.png "Dati della fase di progettazione del modello effettivi con ListView")](media\xaml-design-time-listview-models.png#lightbox)

Il vantaggio è che è possibile associare i controlli a una versione statica della fase di progettazione del modello.

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Usare dati della fase di progettazione con proprietà e tipi personalizzati

Per impostazione predefinita, questa funzionalità funziona solo con le proprietà e i controlli della piattaforma. In questa sezione vengono illustrati i passaggi necessari per consentire l'uso di controlli personalizzati come controlli della fase di progettazione, una nuova funzionalità disponibile per i clienti che usano Visual Studio 2019 versione [16,8](/visualstudio/releases/2019/release-notes/) o successiva. Esistono tre requisiti per abilitare questa operazione:

- Uno spazio dei nomi xmlns personalizzato

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Versione della fase di progettazione dello spazio dei nomi. Questa operazione può essere eseguita semplicemente aggiungendo/design alla fine.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Aggiunta del prefisso della fase di progettazione a MC: Ignorable

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Dopo aver eseguito tutti questi passaggi, è possibile usare il `myDesignTimeControls` prefisso per creare i controlli della fase di progettazione.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Creazione di uno spazio dei nomi xmlns personalizzato

Per creare uno spazio dei nomi xmlns personalizzato in WPF .NET Core, è necessario eseguire il mapping dello spazio dei nomi XML personalizzato allo spazio dei nomi CLR in cui si trovano i controlli. A tale scopo, è possibile aggiungere l' `XmlnsDefinition` attributo a livello di assembly nel `AssemblyInfo.cs` file. Il file si trova nella gerarchia radice del progetto.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verifica un problema non elencato in questa sezione, è possibile segnalarlo usando lo strumento [segnala un problema](../ide/how-to-report-a-problem-with-visual-studio.md) .

### <a name="requirements"></a>Requisiti

- I dati della fase di progettazione richiedono Visual Studio 2019 versione [16,7](/visualstudio/releases/2019/release-notes) o successiva.

- Supporta i progetti desktop di Windows destinati a Windows Presentation Foundation (WPF) per .NET Core e UWP. Questa funzionalità è disponibile anche per .NET Framework se è stata abilitata la funzionalità di anteprima "nuova finestra di progettazione XAML WPF per .NET Framework".

- A partire da Visual Studio 2019 versione 16,7, questa funzionalità funziona con tutti i controlli predefiniti di WPF e UWP Framework. Il supporto per i controlli di terze parti è ora disponibile nella versione di anteprima 16,8.

### <a name="the-xaml-designer-stopped-working"></a>Il finestra di progettazione XAML ha smesso di funzionare

Provare a chiudere e riaprire il file XAML e a pulire e ricompilare il progetto.

## <a name="see-also"></a>Vedere anche

- [Dati della fase di progettazione con il Visualizzatore anteprima Novell. Forms](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [XAML in all WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)