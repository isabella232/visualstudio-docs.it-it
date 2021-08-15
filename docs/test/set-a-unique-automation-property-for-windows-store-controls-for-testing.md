---
title: 'Impostare una proprietà di automazione univoca: test dei controlli UWP'
description: Informazioni su come assegnare una proprietà di automazione univoca in base al tipo di controllo XAML nell'applicazione UWP basata su XAML per eseguire un test codificato dell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 73ccfe2ec8562e27f284082c8cd0f577427b01c937ad32b77e0c6cea16787f47
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315096"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Impostare una proprietà di automazione univoca dei controlli UWP per il test

Per eseguire test codificati dell'interfaccia utente per un'applicazione UWP basata su XAML, ogni controllo deve essere identificato da una proprietà di automazione univoca. È possibile assegnare una proprietà di automazione univoca in base al tipo di controllo XAML nell'applicazione.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Definizione XAML statica

Per specificare una proprietà di automazione univoca per un controllo definito nel file XAML, è possibile impostare **AutomationProperties.AutomationId** o **AutomationProperties.Name in** modo implicito o esplicito, come illustrato negli esempi seguenti. Quando si imposta uno di questi valori, al controllo viene assegnata una proprietà di automazione univoca che può essere usata per identificare il controllo quando si crea una registrazione delle azioni o di un test codificato dell'interfaccia utente.

### <a name="set-the-property-implicitly"></a>Impostare la proprietà in modo implicito

Impostare **AutomationProperties.AutomationId** su **ButtonX** tramite la proprietà **Name** nel file XAML per il controllo.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Impostare **AutomationProperties.Name** su **ButtonY** tramite la proprietà **Content** nel file XAML per il controllo.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Impostare la proprietà in modo esplicito

Impostare **AutomationProperties.AutomationId** su **ButtonX** in modo esplicito nel file XAML per il controllo.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Impostare **AutomationProperties.Name** su **ButtonY** in modo esplicito nel file XAML per il controllo.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Assegnare nomi univoci

In Blend per Visual Studio è possibile selezionare un'opzione per assegnare nomi univoci a elementi interattivi quali pulsanti, caselle di riepilogo, caselle combinate e caselle di testo. In questo modo, ai controlli vengono assegnati valori univoci di **AutomationProperties.Name**.

Per assegnare nomi univoci ai controlli esistenti, selezionare **Strumenti**  >  **Assegna nome a elementi interattivi.**

![Denominare elementi interattivi in Blend per Visual Studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Per assegnare automaticamente nomi univoci ai nuovi controlli aggiunti, selezionare **Opzioni**  >  **strumenti** per aprire la finestra **di dialogo** Opzioni. Selezionare **Finestra di progettazione XAML** e **Assegna automaticamente un nome agli elementi interattivi durante la creazione**. Selezionare **OK** per chiudere la finestra di dialogo.

## <a name="use-a-data-template"></a>Usare un modello di dati

Per definire un modello semplice che usa **ItemTemplate** per associare i valori di una casella di riepilogo alle variabili:

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

Per associare i valori alle variabili è anche possibile usare un modello con **ItemContainerStyle**:

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemContainerStyle>
      <Style TargetType="ListBoxItem">
         <Setter Property="Template">
            <Setter.Value>
               <ControlTemplate TargetType="ListBoxItem">
                  <Grid>
                     <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                  </Grid>
               </ControlTemplate>
            </Setter.Value>
         </Setter>
      </Style>
   </ListBox.ItemContainerStyle>
</ListBox>
```

Per entrambi questi esempi, è quindi necessario eseguire l'override del metodo **ToString()** di **ItemSource**, come illustrato nell'esempio di codice seguente. Questo codice consente di verificare che il valore di **AutomationProperties.Name** sia impostato e univoco, dal momento che non è possibile impostare una proprietà di automazione univoca per ogni elemento elenco associato a dati. In questo caso è sufficiente impostare un valore univoco per **Automation Properties.Name**.

> [!NOTE]
> Con questo approccio è anche possibile usare l'associazione per impostare il contenuto interno dell'elemento elenco su una stringa della classe Employee. Come illustrato nell'esempio, al controllo pulsante all'interno di ogni elemento dell'elenco viene assegnato un ID automazione univoco che corrisponde all'ID dipendente.

```csharp
Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}
```

## <a name="use-a-control-template"></a>Usare un modello del controllo

È possibile usare un modello di controllo per fare in modo che ogni istanza di un tipo specifico ottenga una proprietà di automazione univoca quando viene definita nel codice. Creare il modello in modo che **AutomationProperty** sia associato a un ID univoco nell'istanza del controllo. Il codice XAML seguente illustra un approccio per la creazione di questa associazione con un modello del controllo:

```xaml
<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>
```

Quando si definiscono due istanze di un pulsante con questo modello di controllo, l'ID automazione viene impostato sulla stringa di contenuto univoca per i controlli nel modello, come illustrato nel codice XAML seguente:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Controlli dinamici

Se sono presenti controlli creati dinamicamente dal codice e non creati in modo statico o tramite modelli nei file XAML, è necessario impostare le proprietà **Content** o **Name** per il controllo, per fare in modo che a ogni controllo dinamico sia associata una proprietà di automazione univoca. Ad esempio, se è presente una casella di controllo che deve essere visualizzata quando si seleziona un elemento elenco, è possibile impostare queste proprietà, come illustrato di seguito:

```csharp
private void CreateCheckBox(string txt, StackPanel panel)
{
   CheckBox cb = new CheckBox();
   cb.Content = txt; // Sets the AutomationProperties.Name
   cb.Height = 50;
   cb.Width = 100;
   cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
   panel.Children.Add(cb);
}
```

## <a name="see-also"></a>Vedi anche

- [Testare le app UWP con test codificati dell'interfaccia utente](../test/test-uwp-app-with-coded-ui-test.md)
