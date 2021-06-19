---
title: Aggiungere proprietà personalizzate ai diagrammi delle dipendenze
description: Informazioni su come archiviare i valori con qualsiasi elemento in un diagramma delle dipendenze quando si scrive il codice di estensione per i diagrammi delle dipendenze.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70588a2d472a1170b58911eece4fa70831064f72
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389852"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Aggiungere proprietà personalizzate ai diagrammi delle dipendenze

Quando si scrive il codice di estensione per i diagrammi delle dipendenze, è possibile archiviare i valori con qualsiasi elemento in un diagramma delle dipendenze. I valori saranno permanenti quando il diagramma viene salvato e riaperto. È anche possibile fare in modo che queste proprietà vengano visualizzate nella **finestra** Proprietà in modo che gli utenti possano vederle e modificarle. Ad esempio, è possibile consentire agli utenti di specificare un'espressione regolare per ogni livello e scrivere il codice di convalida per verificare che i nomi delle classi in ogni livello siano conformi al modello specificato dall'utente.

## <a name="non-visible-properties"></a>Proprietà non visibili

Se si vuole solo che il codice allegare valori a qualsiasi elemento in un diagramma delle dipendenze, non è necessario definire un componente MEF. Esiste un dizionario denominato `Properties` in [ILayerElement.](/previous-versions/ff644511(v=vs.140)) Aggiungere semplicemente i valori marshalable al dizionario di qualsiasi elemento del livello. Verranno salvati come parte del diagramma delle dipendenze.

## <a name="editable-properties"></a>Proprietà modificabili

**Preparazione iniziale**

> [!IMPORTANT]
> Per visualizzare le proprietà, apportare la modifica seguente in ogni computer in cui si desidera che le proprietà del livello siano visibili:
>
> 1. Eseguire il Blocco note usando **Esegui come amministratore**. Aprire *%ProgramFiles%\Microsoft Visual Studio [versione]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. **All'interno dell'elemento Content** aggiungere:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. Nella sezione **Strumenti di Visual Studio** del menu Start Visual Studio'applicazione aprire **Prompt dei comandi per gli sviluppatori**. Digitare:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Riavviare Visual Studio.

**Assicurarsi che il codice sia in un progetto VSIX**

Se la proprietà fa parte di un progetto di comando, movimento o convalida, non è necessario aggiungere alcun elemento. Il codice per la proprietà personalizzata deve essere specificato in un progetto Extensibility di Visual Studio definito come componente MEF. Per altre informazioni, vedere [Aggiungere comandi](../modeling/add-commands-and-gestures-to-layer-diagrams.md) e movimenti ai diagrammi delle dipendenze o Aggiungere la [convalida dell'architettura personalizzata ai diagrammi delle dipendenze.](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

**Definire la proprietà personalizzata**

Per creare una proprietà personalizzata, definire una classe come quella seguente:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

È possibile definire le proprietà [in ILayerElement](/previous-versions/ff644511(v=vs.140)) o in una delle relative classi derivate, tra cui:

- `ILayerModel` : modello

- `ILayer` - ogni livello

- `ILayerDependencyLink` : collegamenti tra livelli

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

## <a name="see-also"></a>Vedi anche

- [Estendere i diagrammi delle dipendenze](../modeling/extend-layer-diagrams.md)
