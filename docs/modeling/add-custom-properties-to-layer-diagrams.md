---
title: Aggiungere proprietà personalizzate ai diagrammi delle dipendenze
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3623a0c2380188cbb16f6186bddc3f3f2f0c3bd7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590592"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Aggiungere proprietà personalizzate ai diagrammi delle dipendenze

Quando si scrive il codice di estensione per i diagrammi di dipendenza, è possibile archiviare i valori con qualsiasi elemento in un diagramma delle dipendenze. I valori saranno permanenti quando il diagramma viene salvato e riaperto. È anche possibile fare in modo che queste proprietà vengano visualizzate nella finestra **Proprietà** in modo che gli utenti possano visualizzarle e modificarle. Ad esempio, è possibile consentire agli utenti di specificare un'espressione regolare per ogni livello e scrivere il codice di convalida per verificare che i nomi delle classi in ogni livello siano conformi al modello specificato dall'utente.

## <a name="non-visible-properties"></a>Proprietà non visibili

Se si desidera che il codice alleghi valori a qualsiasi elemento in un diagramma delle dipendenze, non è necessario definire un componente MEF. In [ILayerElement](/previous-versions/ff644511(v=vs.140)) è presente un dizionario denominato `Properties`. Aggiungere semplicemente i valori marshalable al dizionario di qualsiasi elemento del livello. Verranno salvati come parte del diagramma delle dipendenze.

## <a name="editable-properties"></a>Proprietà modificabili

**Preparazione iniziale**

> [!IMPORTANT]
> Per visualizzare le proprietà, apportare le modifiche seguenti in ogni computer in cui si desidera che le proprietà del livello siano visibili:
>
> 1. Eseguire il blocco note usando **Esegui come amministratore**. Aprire *%ProgramFiles%\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. All'interno dell'elemento **Content** aggiungere:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. Nella sezione **strumenti di Visual Studio** del menu Start dell'applicazione di Visual Studio aprire **prompt dei comandi per gli sviluppatori**. Immettere
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Riavviare Visual Studio.

**Verificare che il codice si trovi in un progetto VSIX**

Se la proprietà fa parte di un comando, di un movimento o di un progetto di convalida, non è necessario aggiungere alcun elemento. Il codice per la proprietà personalizzata deve essere specificato in un progetto Extensibility di Visual Studio definito come componente MEF. Per altre informazioni, vedere [aggiungere comandi e movimenti a diagrammi di dipendenza](../modeling/add-commands-and-gestures-to-layer-diagrams.md) o [aggiungere la convalida dell'architettura personalizzata ai diagrammi delle dipendenze](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Definire la proprietà personalizzata**

Per creare una proprietà personalizzata, definire una classe come quella seguente:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

È possibile definire le proprietà in [ILayerElement](/previous-versions/ff644511(v=vs.140)) o in una delle classi derivate, incluse le seguenti:

- `ILayerModel` - il modello

- `ILayer` - ciascun livello

- `ILayerDependencyLink` - i collegamenti tra i livelli

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Esempio

Il codice seguente è un descrittore di proprietà personalizzate tipico. Definisce una proprietà booleana nel modello di livello (`ILayerModel`) che consente all'utente di specificare i valori per un metodo di convalida personalizzata.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Vedere anche

- [Estendere i diagrammi delle dipendenze](../modeling/extend-layer-diagrams.md)
