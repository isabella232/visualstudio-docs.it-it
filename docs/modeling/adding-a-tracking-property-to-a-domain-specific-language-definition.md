---
title: Aggiungere la proprietà di rilevamento alla definizione DSL
description: Informazioni sulla proprietà del dominio di rilevamento e su come aggiungere una proprietà di rilevamento a un modello di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 546636ec3de4656bf0f6480dfaa5141d38e963d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384915"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Aggiungere una proprietà di rilevamento alla definizione di un linguaggio specifico di dominio

Questa procedura dettagliata illustra come aggiungere una proprietà di rilevamento a un modello di dominio.

Una *proprietà di dominio* di rilevamento è una proprietà che può essere aggiornata dall'utente, ma che ha un valore predefinito calcolato usando i valori di altre proprietà o elementi del dominio.

Ad esempio, in Domain-Specific Language Tools (strumenti DSL) la proprietà Nome visualizzato di una classe di dominio ha un valore predefinito calcolato usando il nome della classe di dominio, ma un utente può modificare il valore in fase di progettazione o reimpostarlo sul valore calcolato.

In questa procedura dettagliata viene creato un linguaggio specifico di dominio (DSL) con una proprietà di rilevamento dello spazio dei nomi con un valore predefinito basato sulla proprietà Spazio dei nomi predefinito del modello. Per altre informazioni sulle proprietà di rilevamento, vedere [Definizione delle proprietà di rilevamento](/previous-versions/cc825929(v=vs.100)).

- Gli strumenti DSL supportano i descrittori delle proprietà di rilevamento. Tuttavia, la finestra di progettazione DSL non può essere usata per aggiungere una proprietà di rilevamento a un linguaggio. Pertanto, è necessario aggiungere codice personalizzato per definire e implementare la proprietà di rilevamento.

  Una proprietà di rilevamento ha due stati: rilevamento e aggiornamento da parte dell'utente. Le proprietà di rilevamento hanno le funzionalità seguenti:

- Quando si trova nello stato di rilevamento, viene calcolato il valore della proprietà di rilevamento e il valore viene aggiornato quando cambiano le altre proprietà nel modello.

- Quando si è aggiornato in base allo stato dell'utente, il valore della proprietà di rilevamento mantiene il valore su cui l'ultimo utente ha impostato la proprietà.

- Nella finestra **Proprietà** il **comando Reimposta** per la proprietà di rilevamento è abilitato solo quando la proprietà è nello stato aggiornato dall'utente. Il **comando Reimposta** imposta lo stato della proprietà di rilevamento sul rilevamento.

- Nella finestra **Proprietà,** quando la proprietà di rilevamento è nello stato di rilevamento, il relativo valore viene visualizzato con un tipo di carattere normale.

- Nella finestra **Proprietà,** quando la proprietà di rilevamento si trova nello stato aggiornato dall'utente, il relativo valore viene visualizzato in grassetto.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare questa procedura dettagliata, è necessario installare questi componenti:

| Componente | Collegamento |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](https://code.msdn.microsoft.com/site/search?query=%22Modeling%20SDK%22&f%5B0%5D.Value=%22Modeling%20SDK%22&f%5B0%5D.Type=SearchText&ac=5) |

## <a name="create-the-project"></a>Creare il progetto

1. Creare un progetto Domain-Specific Language Designer. Denomina tale elemento `TrackingPropertyDSL`.

2. Nella procedura **Finestra di progettazione Domain-Specific Language guidata** impostare le opzioni seguenti:

    1. Selezionare il **modello MinimalLanguage.**

    2. Usare il nome predefinito per il linguaggio specifico di dominio, `TrackingPropertyDSL` .

    3. Impostare l'estensione per i file di modello su `trackingPropertyDsl` .

    4. Usare l'icona del modello predefinita per i file di modello.

    5. Impostare il nome del prodotto su `Product Name` .

    6. Impostare il nome della società su `Company Name` .

    7. Usare il valore predefinito per lo spazio dei nomi radice per i progetti nella soluzione , `CompanyName.ProductName.TrackingPropertyDSL` .

    8. Consentire alla procedura guidata di creare un file di chiave con nome sicuro per gli assembly.

    9. Esaminare i dettagli della soluzione e quindi fare clic su **Fine** per creare il progetto di definizione DSL.

## <a name="customize-the-default-dsl-definition"></a>Personalizzare la definizione DSL predefinita
 In questa sezione si personalizza la definizione DSL in modo da contenere gli elementi seguenti:

- Proprietà di rilevamento dello spazio dei nomi per ogni elemento del modello.

- Proprietà IsNamespaceTracking booleana per ogni elemento del modello. Questa proprietà indicherà se la proprietà di rilevamento si trova nello stato di rilevamento o nello stato aggiornato dall'utente.

- Proprietà Spazio dei nomi predefinito per il modello. Questa proprietà verrà usata per calcolare il valore predefinito della proprietà Di rilevamento dello spazio dei nomi.

- Proprietà calcolata CustomElements per il modello. Questa proprietà indicherà la percentuale di elementi con uno spazio dei nomi personalizzato.

### <a name="to-add-the-domain-properties"></a>Per aggiungere le proprietà del dominio

1. Nella finestra di progettazione DSL fare clic con il pulsante destro del mouse sulla classe di dominio **ExampleModel,** scegliere **Aggiungi** e quindi fare clic **su DomainProperty**.

    1. Assegnare alla nuova proprietà il nome `DefaultNamespace` .

    2. Nella finestra **Proprietà** per la nuova proprietà impostare **Valore predefinito** su e `DefaultNamespace` impostare **Tipo** su **Stringa**.

2. Alla classe **di dominio ExampleModel** aggiungere una proprietà di dominio denominata `CustomElements` .

     Nella finestra **Proprietà** per la nuova proprietà impostare **Kind su** **Calculated**.

3. Alla classe **di dominio ExampleElement** aggiungere una proprietà di dominio denominata `Namespace` .

     Nella finestra **Proprietà** per la nuova proprietà impostare **Is Browsable** su **False** e **Kind** su **CustomStorage**.

4. Alla classe **di dominio ExampleElement** aggiungere una proprietà di dominio denominata `IsNamespaceTracking` .

     Nella finestra **Proprietà** per la nuova proprietà impostare **Is Browsable** su **False,** impostare **Default Value** su e `true` impostare **Type** su **Boolean**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Per aggiornare gli elementi del diagramma e i dettagli DSL

1. Nella finestra di progettazione DSL fare clic con il pulsante destro del mouse sulla forma **Geometry ExampleShape,** scegliere **Aggiungi** e quindi fare clic su **Decorator di testo**.

    1. Assegnare al nuovo elemento Decorator di testo il nome `NamespaceDecorator` .

    2. Nella finestra **Proprietà** per l'elemento Decorator di testo impostare **Position** su **InnerBottomLeft**.

2. Nella finestra di progettazione DSL selezionare la linea che connette la **classe ExampleElement** alla **forma ExampleShape.**

    1. Nella finestra **Dettagli DSL** selezionare la scheda **Mappe decorator.**

    2. **Nell'elenco Decorator** selezionare **NamespaceDecorator**, selezionare la relativa casella di controllo e quindi nell'elenco **Proprietà** di visualizzazione selezionare Spazio **dei nomi**.

3. In **Esplora DSL** espandere la cartella **Classi di** dominio, fare clic con il pulsante destro del mouse sul nodo **ExampleElement** e quindi scegliere Aggiungi nuovo **descrittore di tipo di dominio**.

    1. Espandere il **nodo ExampleElement** e selezionare il **nodo Custom Type Descriptor (Domain Type Descriptor).**

    2. Nella finestra **Proprietà** per il descrittore del tipo di dominio impostare **Custom Coded** su **True.**

4. In **Esplora linguaggio DSL** selezionare il **nodo Comportamento di serializzazione XML.**

    1. Nella finestra **Proprietà** impostare **Custom Post Load** su **True.**

## <a name="transform-templates"></a>Trasformare i modelli

Dopo aver definito le classi di dominio e le proprietà per il DSL, è possibile verificare che la definizione DSL possa essere trasformata correttamente per rigenerare il codice per il progetto.

1. Sulla barra **Esplora soluzioni** fare clic su **Trasforma tutti i modelli**.

2. Il sistema rigenera il codice per la soluzione e salva DslDefinition.dsl. Per informazioni sul formato XML dei file di definizione, vedere [File DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Creare file per codice personalizzato

Quando si trasformano tutti i modelli, il sistema genera il codice sorgente che definisce il linguaggio specifico di dominio nei progetti Dsl e DslPackage. Per evitare interferenze con il testo generato, scrivere il codice personalizzato in file distinti dai file di codice generati.

È necessario fornire il codice per gestire il valore e lo stato della proprietà di rilevamento. Per distinguere il codice personalizzato dal codice generato ed evitare conflitti di denominazione dei file, inserire i file di codice personalizzati in una sottocartella separata.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto DSL,** scegliere **Aggiungi** e quindi fare clic su **Nuova cartella**. Assegnare alla nuova cartella il nome `CustomCode` .

2. Fare clic con il pulsante destro **del mouse sulla nuova cartella CustomCode,** scegliere **Aggiungi** e quindi fare clic su **Nuovo elemento**.

3. Selezionare il **modello File di** codice, impostare **Nome** su e quindi fare clic `NamespaceTrackingProperty.cs` su **OK.**

     Il file NamespaceTrackingProperty.cs viene creato e aperto per la modifica.

4. Nella cartella creare i file di codice seguenti: `ExampleModel.cs,``HelperClasses.cs` , `Serialization.cs` e `TypeDescriptor.cs` .

5. Nel progetto **DslPackage** creare anche una `CustomCode` cartella e aggiungerne un `Package.cs` file di codice.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Aggiungere classi helper per supportare le proprietà di rilevamento

Al file HelperClasses.cs aggiungere le `TrackingHelper` classi e come indicato di `CriticalException` seguito. Si farà riferimento a queste classi più avanti in questa procedura dettagliata.

1. Aggiungere il codice seguente al file HelperClasses.cs.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Aggiungere codice personalizzato per il descrittore di tipo personalizzato

Implementare `GetCustomProperties` il metodo per il descrittore di tipo per la classe di `ExampleModel` dominio.

> [!NOTE]
> Il codice generato da Strumenti DSL per il descrittore di tipo personalizzato per le chiamate . Tuttavia, gli strumenti DSL non generano codice `ExampleModel` che implementa il metodo `GetCustomProperties` .

La definizione di questo metodo crea il descrittore della proprietà di rilevamento per la proprietà di rilevamento dello spazio dei nomi. Inoltre, la specifica di attributi per la proprietà di rilevamento consente alla **finestra Proprietà** di visualizzare correttamente la proprietà.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Per modificare il descrittore di tipo per la classe di dominio ExampleModel

1. Aggiungere il codice seguente al file TypeDescriptor.cs.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>Aggiunta di codice personalizzato per il pacchetto

Il codice generato definisce un provider di descrizione del tipo per la classe di dominio ExampleElement. Tuttavia, è necessario aggiungere codice per indicare al DSL di usare questo provider di descrizione del tipo.

1. Aggiungere il codice seguente al file Package.cs.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-model"></a>Aggiungere codice personalizzato per il modello

Implementare `GetCustomElementsValue` il metodo per la classe di `ExampleModel` dominio.

> [!NOTE]
> Il codice generato da Strumenti DSL per le chiamate , tuttavia, gli `ExampleModel` strumenti DSL non generano codice `GetCustomElementsValue` che implementa il metodo .

La definizione del `GetCustomElementsValue` metodo fornisce la logica per la proprietà calcolata CustomElements di `ExampleModel` . Questo metodo conta il numero di classi di dominio con una proprietà di rilevamento dello spazio dei nomi con un valore aggiornato dall'utente e restituisce una stringa che rappresenta questo conteggio come percentuale degli elementi totali `ExampleElement` nel modello.

Aggiungere inoltre un metodo a `OnDefaultNamespaceChanged` `ExampleModel` ed eseguire l'override del `OnValueChanged` metodo della classe `DefaultNamespacePropertyHandler` annidata di per chiamare `ExampleModel` `OnDefaultNamespaceChanged` .

Poiché la proprietà DefaultNamespace viene usata per calcolare la proprietà Di rilevamento dello spazio dei nomi, è necessario notificare a tutte le classi di dominio che il `ExampleModel` `ExampleElement` valore di DefaultNamespace è stato modificato.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Per modificare il gestore della proprietà per la proprietà rilevata

1. Aggiungere il codice seguente al file ExampleModel.cs.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-for-the-tracking-property"></a>Aggiungere codice personalizzato per la proprietà Tracking

Aggiungere un `CalculateNamespace` metodo alla classe di `ExampleElement` dominio.

La definizione di questo metodo fornisce la logica per la proprietà calcolata CustomElements di `ExampleModel` . Questo metodo conta il numero di classi di dominio con una proprietà di rilevamento dello spazio dei nomi che si trova nello stato aggiornato dall'utente e restituisce una stringa che rappresenta questo conteggio come percentuale degli elementi totali nel `ExampleElement` modello.

Aggiungere anche l'archiviazione per e i metodi da ottenere e impostare, la proprietà di archiviazione personalizzata Spazio dei nomi della `ExampleElement` classe di dominio.

> [!NOTE]
> Il codice generato da Strumenti DSL per chiama i metodi get e set. Tuttavia, gli strumenti DSL non generano codice `ExampleModel` che implementa i metodi.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Per aggiungere il metodo per il descrittore di tipo personalizzato

1. Aggiungere il codice seguente al file NamespaceTrackingProperty.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-to-support-serialization"></a>Aggiungere codice personalizzato per supportare la serializzazione

Aggiungere codice per supportare il comportamento di post-caricamento personalizzato per la serializzazione XML.

> [!NOTE]
> Il codice generato da Strumenti DSL chiama i metodi e . Tuttavia, gli strumenti DSL non generano codice `OnPostLoadModel` `OnPostLoadModelAndDiagram` che implementa questi metodi.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Per aggiungere codice per supportare il comportamento di post-caricamento personalizzato

1. Aggiungere il codice seguente al file Serialization.cs.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="test-the-language"></a>Testare la lingua

Il passaggio successivo consiste nel compilare ed eseguire la finestra di progettazione DSL in una nuova istanza di in modo che sia possibile verificare che la proprietà di rilevamento [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] funzioni correttamente.

1. Nel menu **Compila** fare clic su **Ricompila soluzione**.

2. Scegliere **Avvia debug** dal menu **Debug**.

    La build sperimentale [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] di apre la soluzione **Debug,** che contiene un file di test vuoto.

3. In **Esplora soluzioni** fare doppio clic sul file Test.trackingPropertyDsl per aprirlo nella finestra di progettazione e quindi fare clic sull'area di progettazione.

    Si noti che nella finestra **Proprietà** per il diagramma la proprietà **Spazio** dei nomi predefinito è **DefaultNamespace** e la proprietà **Elementi** personalizzati è **0/0.**

4. Trascinare **un elemento ExampleElement** dalla **Casella degli strumenti** all'area del diagramma.

5. Nella finestra **Proprietà** per l'elemento selezionare la proprietà **Spazio dei** nomi elemento e modificare il valore da **DefaultNamespace** ad **OtherNamespace**.

    Si noti che il valore di **Spazio dei nomi dell'elemento** è ora visualizzato in grassetto.

6. Nella finestra **Proprietà fare** clic con il pulsante destro del mouse su Spazio dei **nomi elemento** e quindi scegliere **Reimposta**.

    Il valore della proprietà viene modificato in **DefaultNamespace** e il valore viene visualizzato con un tipo di carattere normale.

    Fare di nuovo clic con il **pulsante destro del mouse su Spazio dei nomi dell'elemento.** Il **comando Reimposta** è ora disabilitato perché la proprietà è attualmente nello stato di rilevamento.

7. Trascinare **un altro Elemento ExampleElement** dalla Casella degli **strumenti** all'area del diagramma e modificarne lo spazio dei **nomi dell'elemento** in **OtherNamespace**.

8. Fare clic sull'area di progettazione.

    Nella finestra **Proprietà** del diagramma il valore di **Elementi personalizzati** è **ora 1/2.**

9. Modificare **Lo spazio dei nomi** predefinito per il diagramma da **DefaultNamespace** a **NewNamespace**.

     Lo **spazio dei** nomi del primo elemento  tiene traccia della proprietà **Spazio** dei nomi predefinito, mentre lo spazio dei nomi del secondo elemento mantiene il valore aggiornato dall'utente **OtherNamespace**.

10. Salvare la soluzione e quindi chiudere la compilazione sperimentale.

## <a name="next-steps"></a>Passaggi successivi

Se si prevede di usare più proprietà di rilevamento o di implementare le proprietà di rilevamento in più DSL, è possibile creare un modello di testo per generare il codice comune per il supporto di ogni proprietà di rilevamento. Per altre informazioni sui modelli di testo, vedere [Generazione del codice e Modelli di testo T4.](../modeling/code-generation-and-t4-text-templates.md)

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Procedura: Creare una soluzione per un linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md)