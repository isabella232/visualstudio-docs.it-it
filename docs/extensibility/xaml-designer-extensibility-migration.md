---
title: Migrazione di estensibilità di progettazione XAML
ms.date: 04/17/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: f83c40a67dc36301816b2384242d790a9f776044
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447359"
---
# <a name="xaml-designer-extensibility-migration"></a>Migrazione di estensibilità di progettazione XAML

A partire da Visual Studio 2019 versione 16.1 come anteprima pubblica, la finestra di progettazione XAML supporta due architetture diverse: l'architettura di isolamento della finestra di progettazione e l'architettura più recente di isolamento della superficie. Questa transizione di architettura è necessario per supportare il runtime di destinazione che non possono essere ospitato in un processo di .NET Framework. Lo spostamento dell'architettura di isolamento della superficie introduce importanti modifiche al modello di estendibilità di terze parti. Questo articolo descrive le modifiche.

**Isolamento della finestra di progettazione** viene usato dalla finestra di progettazione WPF per i progetti destinati a .NET Framework e supporta *. Design. dll* estensioni. Il codice utente, le librerie di controlli e le estensioni di terze parti vengono caricate in un processo esterno (*XDesProc.exe*) con il codice effettivo della finestra di progettazione e i pannelli della finestra di progettazione.

**Isolamento della superficie di attacco** viene usato dalla finestra di progettazione UWP. Viene inoltre utilizzato dalla finestra di progettazione WPF per i progetti destinati a .NET Core. Nel livello di isolamento della superficie, librerie di codice e il controllo utente unica vengono caricate in un processo separato, mentre la finestra di progettazione e i pannelli vengono caricati nel processo di Visual Studio (*DevEnv.exe*). Il runtime usato per l'esecuzione di librerie di codice e il controllo utente è diverso da quella utilizzata da .NET Framework per la progettazione effettivo e il codice di estendibilità di terze parti.

![extensibility-migration-architecture](media/xaml-designer-extensibility-migration-architecture.png)

A causa di questa transizione, architettura delle estensioni di terze parti non sono più vengono caricate nello stesso processo come le librerie di controlli di terze parti. Le estensioni non è più possano hanno dipendenze dirette su librerie di controlli o accedere direttamente agli oggetti di runtime. Le estensioni che sono stati precedentemente scritti per l'architettura di isolamento della finestra di progettazione utilizzando il *Microsoft.Windows.Extensibility.dll* API devono essere migrato a un nuovo approccio per lavorare con l'architettura di isolamento della superficie. In pratica, un'estensione esistente dovrà essere compilato con nuovi assembly di API di estendibilità. I tipi di accesso al controllo di runtime tramite [typeof](/dotnet/csharp/language-reference/keywords/typeof) o istanze di runtime devono essere sostituite o rimosso poiché le librerie di controlli vengono ora caricate in un altro processo.

## <a name="new-extensibility-api-assemblies"></a>Nuovi assembly di API di estendibilità

I nuovi assembly di API di estendibilità sono simili agli assembly di API di estendibilità esistente ma seguono uno schema di denominazione diversi per distinguerle. Analogamente, dello spazio dei nomi sono stati modificati per riflettere i nuovi nomi di assembly.

| Finestra di progettazione isolamento assembly API            | Assembly di isolamento della superficie API                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Individuazione e nuova estensione di file

Invece di usare il *. Design. dll* estensione nuova superficie estensioni verranno individuate tramite il *. designtools.dll* estensione di file. *. Design. dll* e *. designtools.dll* estensioni possono trovarsi nella stessa *progettazione* sottocartella.

Mentre le librerie di controlli di terze parti compilate per il runtime di destinazione effettiva (.NET Core o UWP), il *. designtools.dll* estensione deve sempre essere compilata come assembly .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Separare le tabelle degli attributi da tipi di runtime

Non consente il modello di estendibilità della superficie di isolamento per le estensioni a dipendono le librerie di controlli effettivi e di conseguenza, le estensioni non possono fare riferimento ai tipi dalla libreria di controllo. Ad esempio, *MyLibrary.designtools.dll* non deve avere una dipendenza *MyLibrary. dll*.

Queste dipendenze sono state più comuni durante la registrazione dei metadati per i tipi tramite le tabelle degli attributi. I tipi di codice di estensione che fa riferimento alle libreria di controlli direttamente tramite [typeof](/dotnet/csharp/language-reference/keywords/typeof) viene sostituito con le nuove API con i nomi dei tipi basati su stringa:

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
      AttributeTableBuilder builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

## <a name="feature-providers-and-model-api"></a>Provider di funzionalità e API del modello

Provider di funzionalità vengono implementati nell'assembly delle estensioni e caricati nel processo di Visual Studio. `FeatureAttribute` continueranno a fare riferimento ai tipi di provider di funzionalità usando direttamente [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Poiché i provider di funzionalità vengono ora caricati in un processo diverso da librerie di codice e il controllo di runtime effettivo, non sono più in grado di accedere direttamente agli oggetti di runtime. Al contrario, tutte le interazioni di questo tipo devono essere convertite per utilizzare le API basate su modello corrispondente. L'API del modello è stato aggiornato e l'accesso a <xref:System.Type> oppure <xref:System.Object> può essere non è più disponibile o è stato sostituito con `TypeIdentifier` e `TypeDefinition`.

`TypeIdentifier` rappresenta una stringa senza un nome di assembly che identifica un tipo. Oggetto `TypeIdenfifier` può essere risolta in un `TypeDefinition` per richiedere informazioni aggiuntive sul tipo. `TypeDefinition` non è memorizzabile nella cache le istanze nel codice dell'estensione.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type != null && buttonType != type.IsSubclassOf(buttonType))
{
}
```

API è stato rimosso dal set di API di estendibilità di superficie isolamento:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

Le API che usano `TypeIdentifier` invece di <xref:System.Type>:

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

Le API che usano `TypeIdentifier` invece di <xref:System.Type> e non supporterà più argomenti del costruttore:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

Le API che usano `TypeDefinition` invece di <xref:System.Type>:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`

Le API che usano `ModelItem` invece di <xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Noto come tipi primitivi `int`, `string`, o `Thickness` può essere passato all'API del modello come istanze di .NET Framework e verrà convertito in oggetto corrispondente nel processo di runtime di destinazione. Ad esempio:

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

## <a name="limited-support-for-designdll-extensions"></a>Supporto limitato per. Design. dll estensioni

Eventuale *. designtools.dll* estensione individuata per una libreria di controlli, viene caricata prima e individuazione per *. Design. dll* estensioni viene ignorata.

Se nessun *. designtools.dll* sono presenti estensioni, ma un *. Design. dll* estensione viene trovata, il servizio di linguaggio XAML tenta di caricare l'assembly per estrarre le informazioni della tabella di attributi per il supporto editor di base e gli scenari di controllo della proprietà. Questo meccanismo è limitato nell'ambito. Non consente il caricamento delle estensioni di isolamento della finestra di progettazione per l'esecuzione di provider di funzionalità, ma potrebbe offrire il supporto di base per le librerie di controlli WPF esistenti.
