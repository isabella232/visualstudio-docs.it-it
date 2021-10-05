---
title: Usare i dati di esempio in fase di progettazione con finestra di progettazione XAML in Visual Studio
description: Informazioni su come usare i dati di esempio in fase di progettazione in XAML.
ms.date: 06/01/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
monikerRange: '>=vs-2019'
ms.openlocfilehash: b12ab7e93fbd7c7adab188492853ec4a9230cc7d
ms.sourcegitcommit: 2eb12954b7b0ac9508fff11a86c54e880f3d104f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439808"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Usare i dati di esempio in fase di progettazione con finestra di progettazione XAML in Visual Studio

Alcuni controlli che si rivoluzionano ai dati, ad esempio , e , sono difficili `ListView` `ListBox` da visualizzare senza `DataGrid` dati. In questo articolo verrà esaminato un nuovo approccio che consente agli sviluppatori che lavorano a progetti .NET Core Windows Presentation Foundation (WPF) o progetti wpf .NET Framework con finestra di progettazione XAML in Visual Studio di abilitare i dati di esempio in questi controlli. 

## <a name="requirements"></a>Requisiti

La funzionalità Dati di esempio richiede Visual Studio 2019 [versione 16.10](/visualstudio/releases/2019/release-notes-v16.10) o successiva.

La funzionalità supporta Windows progetti desktop che hanno come destinazione WPF per .NET Core o .NET Framework quando si usa la nuova finestra di progettazione. Per abilitare la nuova finestra di progettazione per .NET Framework:

1. Passare a **Strumenti Opzioni**  >  **Opzioni Funzionalità**  >  **di** anteprima  >  **dell'ambiente**.
2. Selezionare **New WPF finestra di progettazione XAML for .NET Framework**, quindi riavviare Visual Studio.

## <a name="basics-of-the-sample-data-feature"></a>Nozioni di base sulla funzionalità Dati di esempio

La funzionalità Dati di esempio è solo per la visualizzazione in fase di progettazione. Viene visualizzato solo nella finestra di progettazione XAML, non nell'app in esecuzione. Di conseguenza, viene applicato alla versione in fase di progettazione della `ItemsSource` proprietà `d:ItemsSource` . Per il funzionamento dei dati di esempio è necessario che lo spazio dei nomi della fase di progettazione funzioni. 

> [!NOTE]
> Per altre informazioni sulle proprietà della fase di progettazione in XAML, vedere [Proprietà della fase di progettazione XAML.](../xaml-tools/xaml-designtime-data.md)

Per iniziare, aggiungere le righe di codice seguenti all'intestazione del documento XAML, se non sono già presenti:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Dopo aver aggiunto gli spazi dei nomi, è possibile usare per abilitare i dati `d:ItemsSource="{d:SampleData}"` di esempio nel controllo , o `ListView` `Listbox` `DataGrid` . Ad esempio:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![Screenshot che mostra i dati di esempio in una griglia dei dati.](media\xaml-sample-data-empty-datagrid.png "Dati di esempio abilitati in una griglia dati")](media\xaml-sample-data-empty-datagrid.png#lightbox)

In questo esempio, senza `d:ItemsSource="{d:SampleData}"` , il finestra di progettazione XAML mostra una griglia dei dati vuota. Al contrario, `d:SampleData` con , ora vengono visualizzati i dati di esempio predefiniti generati.

Per impostazione predefinita, vengono visualizzati cinque elementi. È tuttavia possibile usare la `ItemCount` proprietà per specificare il numero di elementi da visualizzare. Ad esempio: `d:ItemsSource="{d:SampleData ItemCount=2}"`.

## <a name="sample-data-with-data-templates"></a>Dati di esempio con modelli di dati

La funzionalità Dati di esempio funziona per `ListBox` i controlli , o quando si usano modelli di `ListView` `DataGrid` dati. La funzionalità analerà `DataTemplate` il controllo e tenterà di generare i dati appropriati. 

I dati di esempio verranno generati solo per gli elementi nei modelli di dati che usano associazioni. I dati di esempio verranno generati anche se le associazioni non hanno ancora un'origine. Ad esempio:

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![Screenshot che mostra i dati di esempio in una visualizzazione elenco con un modello di dati.](media\xaml-sample-data-templated-listview.png "Dati di esempio usati in una visualizzazione elenco con un modello di dati")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="sample-data-with-suggested-actions"></a>Dati di esempio con azioni suggerite

Per abilitare o disabilitare facilmente i dati di esempio per un controllo dalla finestra di progettazione, è possibile usare la funzionalità Azioni suggerite. Azioni suggerite è una lampadina nella finestra di progettazione visualizzata in alto a destra quando si seleziona un controllo. È possibile abilitare i dati di esempio selezionando il controllo, selezionando la lampadina e quindi **selezionando Mostra dati di esempio**. Ad esempio:

[![Screenshot che mostra i dati di esempio con Azioni suggerite.](media\xaml-sample-data-suggested-actions.png "Abilitare i dati di esempio con Azioni suggerite")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-the-ivalueconverter-interface"></a>Dati di esempio con l'interfaccia IValueConverter 

La funzionalità Dati di esempio non supporta completamente i convertitori o `IValueConverter` l'interfaccia. È tuttavia possibile farlo funzionare eseguendo una o entrambe le operazioni seguenti:

- Assicurarsi che la `Convert` funzione possa gestire uno scenario in cui il valore è già il tipo di destinazione.
- Implementare `ConvertBack` la funzione che riconvertirà il valore nel tipo originale. 

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se i dati di esempio non mostrano nulla o non visualizzano il tipo corretto, è possibile provare ad aggiornare la finestra di progettazione o chiudere e riaprire la pagina.

Se si verifica un problema che non è elencato in questa sezione o che non può essere risolto aggiornando la pagina, segnalarci il problema usando lo strumento Segnala [un](../ide/how-to-report-a-problem-with-visual-studio.md) problema.

## <a name="see-also"></a>Vedi anche

- [Proprietà della fase di progettazione XAML](../xaml-tools/xaml-designtime-data.md)
- [XAML in all WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)