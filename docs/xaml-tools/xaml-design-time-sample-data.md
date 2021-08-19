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
ms.openlocfilehash: cf3fbfc29b79d04ae71fa4ba50815b22045997c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114537"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Usare i dati di esempio in fase di progettazione con finestra di progettazione XAML in Visual Studio

Alcuni controlli che si distoglieno i dati, ad esempio ListView, ListBox o DataGrid, sono difficili da visualizzare senza dati. In questo documento verrà esaminato un nuovo approccio che consente agli sviluppatori che lavorano su progetti **WPF .NET Core** o **progetti wpf .NET Framework** con la nuova finestra di progettazione di abilitare i dati di esempio in questi controlli. 

## <a name="sample-data-feature-basics"></a>Nozioni di base sulla funzionalità dei dati di esempio

I dati di esempio sono solo per la visualizzazione in fase di progettazione, ovvero vengono visualizzati solo nella finestra di progettazione XAML, non nell'app in esecuzione. Di conseguenza, viene applicato alla versione in fase di progettazione della proprietà ItemsSource `d:ItemsSource` . Per il funzionamento dei dati di esempio è necessario lo spazio dei nomi della fase di progettazione. Per iniziare, aggiungere le righe di codice seguenti all'intestazione del documento XAML, se non sono già presenti:

> [!NOTE]
> Per [altre informazioni sulle proprietà della](../xaml-tools/xaml-designtime-data.md) fase di progettazione in XAML, vedere Proprietà della fase di progettazione XAML.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Dopo aver aggiunto gli spazi dei nomi, puoi usare per abilitare i dati `d:ItemsSource="{d:SampleData}"` di esempio in ListView, Listbox o DataGrid. Esempio:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![Dati di esempio con DataGrid](media\xaml-sample-data-empty-datagrid.png "Dati di esempio abilitati in datagrid")](media\xaml-sample-data-empty-datagrid.png#lightbox)

In questo esempio, senza `d:ItemsSource="{d:SampleData}"` il finestra di progettazione XAML verrà visualizzato un datagrid vuoto. Al contrario, `d:SampleData` con ora vengono visualizzati i dati di esempio predefiniti generati.

Per impostazione predefinita, vengono visualizzati 5 elementi. È tuttavia possibile usare la **proprietà ItemCount** per specificare il numero di elementi da visualizzare. Per esempio: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>I dati di esempio funzionano con i modelli di dati

Dati di esempio funziona per i controlli ListBox, ListView o DataGrid quando si usano modelli di dati. La funzionalità Dati di esempio analerà il DataTemplate e tenterà di generare i dati appropriati. I dati di esempio verranno generati solo per gli elementi in DataTemplate che usano associazioni. I dati di esempio verranno generati anche se le associazioni non hanno ancora un'origine.
Esempio:

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

[![ListView di dati di esempio con datatemplate](media\xaml-sample-data-templated-listview.png "Dati di esempio usati in un controllo ListView con un DataTemplate")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>Abilitare i dati di esempio con le azioni suggerite

Per abilitare o disabilitare facilmente i dati di esempio per un controllo dalla finestra di progettazione, è possibile usare la funzionalità Azioni suggerite. Suggested Actions (Azioni suggerite) è una lampadina nella finestra di progettazione visualizzata in alto a destra quando si seleziona un controllo. È possibile abilitare Dati di esempio selezionando il controllo, facendo clic sulla lampadina e quindi su `Show Sample Data` . Esempio:

[![Azioni suggerite per i dati di esempio](media\xaml-sample-data-suggested-actions.png "Abilitare i dati di esempio con le azioni suggerite")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>Dati di esempio con IValueConverter 

I convertitori non sono completamente supportati dalla funzionalità Dati di esempio. È tuttavia possibile farlo funzionare eseguendo una o entrambe le operazioni seguenti:
- Assicurarsi che la `Convert` funzione sia in grado di gestire uno scenario in cui il valore è già targetType.

- Implementare `ConvertBack` la funzione che riconvertirà il valore nel tipo originale. 

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se i dati di esempio non mostrano nulla o non visualizzano il tipo corretto, è possibile provare ad aggiornare la finestra di progettazione o chiudere e riaperre la pagina.

Se si verifica un problema che non è elencato in questa sezione o non può essere risolto aggiornando la pagina, segnalarci usando lo strumento Segnala [un](../ide/how-to-report-a-problem-with-visual-studio.md) problema.

### <a name="requirements"></a>Requisiti

- Dati di esempio richiede Visual Studio 2019 [versione 16.10](/visualstudio/releases/2019/release-notes-v16.10) o successiva.

- Supporta Windows desktop che hanno come destinazione Windows Presentation Foundation (WPF) per .NET Core o .NET Framework quando si usa la nuova finestra di progettazione. Per abilitare la nuova finestra di progettazione per .NET Framework passare a Strumenti > Opzioni > Environment > Preview Features (Funzionalità di anteprima dell'ambiente >), selezionare New WPF finestra di progettazione XAML for .NET Framework (Nuovo finestra di progettazione XAML WPF per .NET Framework) e quindi riavviare Visual Studio.

## <a name="see-also"></a>Vedi anche

- [Proprietà della fase di progettazione XAML](../xaml-tools/xaml-designtime-data.md)
- [XAML in all WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)