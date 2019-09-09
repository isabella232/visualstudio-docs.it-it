---
title: Migrazione finestra di progettazione XAML estensibilità
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 6ffa8888529586e23d6f9762c3ec5b724c708ca5
ms.sourcegitcommit: ab2c49ce72ccf44b27b5c8852466d15a910453a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2019
ms.locfileid: "69024552"
---
# <a name="xaml-designer-extensibility-migration"></a>Migrazione di estendibilità della finestra di progettazione XAML

In Visual Studio 2019, la finestra di progettazione XAML supporta due architetture diverse: l'architettura di isolamento della finestra di progettazione e l'architettura di isolamento della superficie più recente. Questa transizione di architettura è necessaria per supportare i runtime di destinazione che non possono essere ospitati in un processo di .NET Framework. Il passaggio all'architettura di isolamento della superficie introduce modifiche di rilievo al modello di estendibilità di terze parti. Questo articolo descrive queste modifiche, disponibili in Visual Studio 2019 a partire dalla versione 16,3.

L' **isolamento della finestra di progettazione** viene utilizzato dalla finestra di progettazione WPF per i progetti destinati a .NET Framework e supporta le estensioni *. Design. dll* . Il codice utente, le librerie di controlli e le estensioni di terze parti vengono caricati in un processo esterno (*XDesProc. exe*) insieme al codice della finestra di progettazione e ai pannelli della finestra di progettazione effettivi.

L' **isolamento della superficie** viene usato da UWP designer. Viene usato anche da WPF Designer per i progetti destinati a .NET Core. Nell'isolamento della superficie, solo il codice utente e le librerie di controlli vengono caricati in un processo separato, mentre la finestra di progettazione e i relativi pannelli vengono caricati nel processo di Visual Studio (*devenv. exe*). Il runtime utilizzato per l'esecuzione di codice utente e librerie di controlli è diverso da quello utilizzato dal .NET Framework per la finestra di progettazione effettiva e il codice di estendibilità di terze parti.

![estendibilità-migrazione-architettura](media/xaml-designer-extensibility-migration-architecture.png)

A causa di questa transizione di architettura, le estensioni di terze parti non vengono più caricate nello stesso processo delle librerie di controlli di terze parti. Le estensioni non possono più avere dipendenze dirette da librerie di controlli o accedere direttamente agli oggetti runtime. Le estensioni scritte in precedenza per l'architettura di isolamento della finestra di progettazione tramite l'API *Microsoft. Windows. Extensibility. dll* devono essere migrate a un nuovo approccio per lavorare con l'architettura di isolamento della superficie. In pratica, è necessario compilare un'estensione esistente a fronte di nuovi assembly dell'API di estendibilità. L'accesso ai tipi di controllo di runtime tramite [typeof](/dotnet/csharp/language-reference/keywords/typeof) o istanze di runtime deve essere sostituito o rimosso perché le librerie di controlli sono ora caricate in un processo diverso.

## <a name="new-extensibility-api-assemblies"></a>Nuovi assembly dell'API di estendibilità

I nuovi assembly dell'API di estensibilità sono simili agli assembly dell'API di estendibilità esistenti, ma seguono uno schema di denominazione diverso per distinguerli. Analogamente, i nomi degli spazi dei nomi sono stati modificati in modo da riflettere i nuovi nomi degli assembly.

| Assembly dell'API di isolamento della finestra di progettazione            | Assembly dell'API di isolamento della superficie                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Nuova estensione di file e individuazione

Anziché utilizzare l'estensione di file *. Design. dll* , le nuove estensioni di superficie verranno individuate utilizzando l'estensione di file *. DesignTools. dll* . le estensioni *. Design. dll* e *. DesignTools. dll* possono esistere nella stessa sottocartella di *progettazione* .

Mentre le librerie di controllo di terze parti vengono compilate per il runtime di destinazione effettivo (.NET Core o UWP), l'estensione *. DesignTools. dll* deve essere sempre compilata come assembly .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Separare le tabelle degli attributi dai tipi di runtime

Il modello di estendibilità dell'isolamento della superficie non consente alle estensioni di dipendere da librerie di controlli effettive e, pertanto, le estensioni non possono fare riferimento ai tipi dalla libreria di controlli. Ad esempio, *MyLibrary. DesignTools. dll* non deve avere una dipendenza da *MyLibrary. dll*.

Tali dipendenze erano più comuni durante la registrazione dei metadati per i tipi tramite le tabelle degli attributi. Il codice di estensione che fa riferimento ai tipi di libreria di controlli direttamente tramite [typeof](/dotnet/csharp/language-reference/keywords/typeof) o [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) viene sostituito nelle nuove API usando nomi di tipo basati su stringa:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      var builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>Provider di funzionalità e API del modello

I provider di funzionalità sono implementati in assembly di estensione e caricati nel processo di Visual Studio. `FeatureAttribute`continuerà a fare riferimento ai tipi di provider di funzionalità direttamente usando [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Attualmente sono supportati i provider di funzionalità seguenti:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`

Poiché i provider di funzionalità sono ora caricati in un processo diverso dalle librerie di controlli e dal codice runtime effettivi, non sono più in grado di accedere direttamente agli oggetti runtime. Al contrario, tutte queste interazioni devono essere convertite in modo da utilizzare le API basate su modello corrispondenti. L'API del modello è stata aggiornata e l'accesso <xref:System.Type> a <xref:System.Object> o non è più disponibile o è stato sostituito con `TypeIdentifier` e `TypeDefinition`.

`TypeIdentifier`rappresenta una stringa senza il nome di un assembly che identifica un tipo. Un `TypeIdenfifier` oggetto può essere risolto in `TypeDefinition` un oggetto per eseguire una query su informazioni aggiuntive sul tipo. `TypeDefinition`le istanze non possono essere memorizzate nella cache nel codice di estensione.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

API rimosse dal set di API di estendibilità dell'isolamento della superficie:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

API che usano `TypeIdentifier` invece di <xref:System.Type>:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

Le API che `TypeIdentifier` usano invece <xref:System.Type> di e non supportano più gli argomenti del costruttore:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

API che usano `TypeDefinition` invece di <xref:System.Type>:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`

API che usano `ModelItem` invece di <xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Inoltre, `ModelItem` le API `SetValue` come supporteranno solo istanze di tipi primitivi o tipi .NET Framework predefiniti che possono essere convertiti per il runtime di destinazione. Attualmente sono supportati i tipi seguenti:

* Tipi di `Boolean`.NET Framework primitivi: `Char`, `DateTime` `Byte`, `Double`, `Enum`,, ,`Int16` ,,`Int32` ,`SByte` ,, `Guid` `Int64` `Nullable` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* `Brush`Tipi di .NET Framework WPF noti (e tipi derivati): `CornerRadius`, `Duration` `Color`, `CompositeTransform`, `EasingMode`, `EllipseGeometry`, `FontFamily` `EasingFunctionBase`, `GeneralTransform`, `Geometry` ,,, , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

Ad esempio:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

Altri esempi di codice sono disponibili nel repository [XAML-Designer-Extensibility-Samples](https://github.com/microsoft/xaml-designer-extensibility-samples) .

## <a name="limited-support-for-designdll-extensions"></a>Supporto limitato per le estensioni. Design. dll

Se viene individuata un'estensione *. DesignTools. dll* per una libreria di controlli, viene caricata per prima e l'individuazione delle estensioni *. Design. dll* viene ignorata.

Se non sono presenti estensioni *. DesignTools. dll* , ma viene trovata un'estensione *. Design. dll* , il servizio di linguaggio XAML tenta di caricare l'assembly per estrarre le informazioni della tabella degli attributi per supportare scenari di base di editor e di controllo proprietà. Questo meccanismo è limitato nell'ambito. Non consente il caricamento delle estensioni di isolamento della finestra di progettazione per eseguire i provider di funzionalità, ma potrebbe fornire supporto di base per le librerie di controlli WPF esistenti.
