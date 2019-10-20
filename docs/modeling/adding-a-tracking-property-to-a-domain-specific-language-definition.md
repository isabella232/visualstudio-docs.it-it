---
title: Aggiungere la proprietà di rilevamento alla definizione DSL
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0fd1fb2bc6440b02e0aad163ee55a7a7f86807a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652281"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Aggiungere una proprietà di rilevamento alla definizione di un linguaggio specifico di dominio

In questa procedura dettagliata viene illustrato come aggiungere una proprietà di rilevamento a un modello di dominio.

Una proprietà del *dominio di rilevamento* è una proprietà che può essere aggiornata dall'utente, ma con un valore predefinito che viene calcolato utilizzando i valori di altre proprietà o elementi del dominio.

Ad esempio, nel Strumenti Domain-Specific Language (strumenti DSL), la proprietà nome visualizzato di una classe di dominio ha un valore predefinito che viene calcolato usando il nome della classe di dominio, ma un utente può modificare il valore in fase di progettazione o reimpostarlo sul valore calcolato.

In questa procedura dettagliata viene creato un linguaggio specifico di dominio (DSL) che dispone di una proprietà di rilevamento dello spazio dei nomi con un valore predefinito basato sulla proprietà dello spazio dei nomi predefinita del modello. Per ulteriori informazioni sulle proprietà di rilevamento, vedere [definizione delle proprietà di rilevamento](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Gli strumenti DSL supportano il rilevamento dei descrittori di proprietà. Tuttavia, non è possibile usare la finestra di progettazione DSL per aggiungere una proprietà di rilevamento a una lingua. Pertanto, è necessario aggiungere codice personalizzato per definire e implementare la proprietà di rilevamento.

  Una proprietà di rilevamento dispone di due stati: rilevamento e aggiornamento da parte dell'utente. Le proprietà di rilevamento includono le funzionalità seguenti:

- Quando si trova nello stato di rilevamento, il valore della proprietà di rilevamento viene calcolato e il valore viene aggiornato mentre le altre proprietà nel modello cambiano.

- Quando nello stato aggiornato da utente, il valore della proprietà di rilevamento mantiene il valore al quale l'utente ha impostato l'ultima proprietà.

- Nella finestra **Proprietà** , il comando **Reimposta** per la proprietà di rilevamento viene abilitato solo quando la proprietà è nello stato aggiornato da utente. Il comando **Reset** imposta lo stato della proprietà Tracking su Tracking.

- Nella finestra **Proprietà** , quando la proprietà di rilevamento è nello stato di rilevamento, il relativo valore viene visualizzato in un tipo di carattere normale.

- Nella finestra **Proprietà** , quando la proprietà Tracking si trova nello stato aggiornato da utente, il relativo valore viene visualizzato in grassetto.

## <a name="prerequisites"></a>Prerequisites

Prima di iniziare questa procedura dettagliata, è necessario installare prima i componenti seguenti:

| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581) |

## <a name="create-the-project"></a>Creare il progetto

1. Creare un progetto Finestra di progettazione Domain-Specific Language. Assegnargli il nome `TrackingPropertyDSL`.

2. Nella **procedura guidata finestra di progettazione Domain-Specific Language**impostare le opzioni seguenti:

    1. Selezionare il modello **MinimalLanguage** .

    2. Utilizzare il nome predefinito per il linguaggio specifico di dominio `TrackingPropertyDSL`.

    3. Impostare l'estensione per i file di modello su `trackingPropertyDsl`.

    4. Utilizzare l'icona del modello predefinito per i file del modello.

    5. Consente di impostare il nome del prodotto su `Product Name`.

    6. Impostare il nome della società su `Company Name`.

    7. Usare il valore predefinito per lo spazio dei nomi radice per i progetti nella soluzione `CompanyName.ProductName.TrackingPropertyDSL`.

    8. Consentire alla procedura guidata di creare un file di chiave con nome sicuro per gli assembly.

    9. Esaminare i dettagli della soluzione, quindi fare clic su **fine** per creare il progetto di definizione DSL.

## <a name="customize-the-default-dsl-definition"></a>Personalizzare la definizione DSL predefinita
 In questa sezione viene personalizzata la definizione DSL in modo da contenere gli elementi seguenti:

- Proprietà di rilevamento dello spazio dei nomi per ogni elemento del modello.

- Proprietà booleana IsNamespaceTracking per ogni elemento del modello. Questa proprietà indicherà se la proprietà di rilevamento è nello stato di rilevamento o nello stato aggiornato da utente.

- Proprietà predefinita dello spazio dei nomi per il modello. Questa proprietà verrà utilizzata per calcolare il valore predefinito della proprietà di rilevamento dello spazio dei nomi.

- Proprietà calcolata CustomElements per il modello. Questa proprietà indicherà la proporzione di elementi che dispongono di uno spazio dei nomi personalizzato.

### <a name="to-add-the-domain-properties"></a>Per aggiungere le proprietà del dominio

1. Nella finestra di progettazione DSL, fare clic con il pulsante destro del mouse sulla classe di dominio **ExampleModel** , scegliere **Aggiungi**, quindi fare clic su **DomainProperty**.

    1. Assegnare un nome alla nuova proprietà `DefaultNamespace`.

    2. Nella finestra **Proprietà** per la nuova proprietà impostare **valore predefinito** su `DefaultNamespace` e impostare **tipo** su **stringa**.

2. Aggiungere una proprietà di dominio denominata `CustomElements` alla classe di dominio **ExampleModel** .

     Nella finestra **Proprietà** per la nuova proprietà impostare **Kind** su **calcolato**.

3. Alla classe di dominio **ExampleElement** aggiungere una proprietà di dominio denominata `Namespace`.

     Nella finestra **Proprietà** per la nuova proprietà impostare **è esplorabile** su **false**e impostare **tipo** su **CustomStorage**.

4. Alla classe di dominio **ExampleElement** aggiungere una proprietà di dominio denominata `IsNamespaceTracking`.

     Nella finestra **Proprietà** per la nuova proprietà impostare **è esplorabile** su **false**, impostare il **valore predefinito** su `true` e impostare **tipo** su **booleano**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Per aggiornare gli elementi del diagramma e i dettagli DSL

1. Nella finestra di progettazione DSL, fare clic con il pulsante destro del mouse sulla forma geometria **ExampleShape** , scegliere **Aggiungi**, quindi fare clic su **elemento Decorator testo**.

    1. Denominare il nuovo elemento Decorator del testo `NamespaceDecorator`.

    2. Nella finestra **Proprietà** per l'elemento Decorator testo impostare **position** su **InnerBottomLeft**.

2. Nella finestra di progettazione DSL selezionare la riga che connette la classe **ExampleElement** alla forma **ExampleShape** .

    1. Nella finestra **Dettagli DSL** selezionare la scheda **mappe elemento Decorator** .

    2. Nell'elenco elementi **Decorator** selezionare **NamespaceDecorator**, selezionare la relativa casella di controllo e quindi nell'elenco **proprietà di visualizzazione** selezionare **spazio dei nomi**.

3. In **DSL Explorer**espandere la cartella **classi di dominio** , fare clic con il pulsante destro del mouse sul nodo **ExampleElement** , quindi scegliere **Aggiungi nuovo descrittore del tipo di dominio**.

    1. Espandere il nodo **ExampleElement** e selezionare il nodo **descrittore del tipo personalizzato (descrittore del tipo di dominio)** .

    2. Nella finestra **Proprietà** per il descrittore del tipo di dominio impostare **Custom coded** su **true**.

4. In **DSL Explorer**selezionare il nodo del **comportamento di serializzazione XML** .

    1. Nella finestra **Proprietà** impostare **Custom Post Load** su **true**.

## <a name="transform-templates"></a>Trasformare i modelli

Ora che sono state definite le classi e le proprietà di dominio per il linguaggio DSL, è possibile verificare che la definizione DSL possa essere trasformata correttamente per rigenerare il codice per il progetto.

1. Sulla barra degli strumenti **Esplora soluzioni** fare clic su **trasforma tutti i modelli**.

2. Il sistema rigenera il codice per la soluzione e Salva DslDefinition. DSL. Per informazioni sul formato XML dei file di definizione, vedere [il file DslDefinition. DSL](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Creare file per codice personalizzato

Quando si trasformano tutti i modelli, il sistema genera il codice sorgente che definisce il linguaggio specifico di dominio nei progetti DSL e DslPackage. Per evitare di interferire con il testo generato, è possibile scrivere il codice personalizzato nei file distinti rispetto ai file di codice generati.

È necessario fornire il codice per la gestione del valore e dello stato della proprietà di rilevamento. Per semplificare la distinzione del codice personalizzato dal codice generato e per evitare conflitti di denominazione dei file, inserire i file di codice personalizzati in una sottocartella separata.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **DSL** , scegliere **Aggiungi**, quindi fare clic su **nuova cartella**. Assegnare alla nuova cartella il nome `CustomCode`.

2. Fare clic con il pulsante destro del mouse sulla nuova cartella **CustomCoded** , scegliere **Aggiungi**, quindi fare clic su **nuovo elemento**.

3. Selezionare il modello **file di codice** , impostare il **nome** su `NamespaceTrackingProperty.cs` e quindi fare clic su **OK**.

     Il file NamespaceTrackingProperty.cs viene creato e aperto per la modifica.

4. Nella cartella creare i file di codice seguenti: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs` e `TypeDescriptor.cs`.

5. Nel progetto **DslPackage** creare inoltre una cartella `CustomCode` e aggiungervi un file di codice `Package.cs`.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Aggiungere classi helper per supportare le proprietà di rilevamento

Aggiungere al file HelperClasses.cs le classi `TrackingHelper` e `CriticalException`, come indicato di seguito. Si faranno riferimento a queste classi più avanti in questa procedura dettagliata.

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

Implementare il metodo `GetCustomProperties` per il descrittore di tipo per la classe di dominio `ExampleModel`.

> [!NOTE]
> Il codice generato dagli strumenti DSL per il descrittore di tipo personalizzato per `ExampleModel` chiama `GetCustomProperties`; Tuttavia, gli strumenti DSL non generano codice che implementi il metodo.

Definendo questo metodo viene creato il descrittore della proprietà di rilevamento per la proprietà di rilevamento dello spazio dei nomi Inoltre, la creazione di attributi per la proprietà di rilevamento consente alla finestra **Proprietà** di visualizzare correttamente la proprietà.

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

Il codice generato definisce un provider di descrizioni dei tipi per la classe di dominio ExampleElement. Tuttavia, è necessario aggiungere il codice per indicare al DSL di utilizzare questo provider di descrizioni dei tipi.

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

Implementare il metodo `GetCustomElementsValue` per la classe di dominio `ExampleModel`.

> [!NOTE]
> Il codice generato dagli strumenti DSL per `ExampleModel` chiama `GetCustomElementsValue`; Tuttavia, gli strumenti DSL non generano codice che implementi il metodo.

La definizione del metodo `GetCustomElementsValue` fornisce la logica per la proprietà calcolata CustomElements di `ExampleModel`. Questo metodo conta il numero di `ExampleElement` classi di dominio che dispongono di una proprietà di rilevamento dello spazio dei nomi con un valore aggiornato dall'utente e restituisce una stringa che rappresenta il conteggio come una percentuale degli elementi totali del modello.

Aggiungere inoltre un metodo `OnDefaultNamespaceChanged` per `ExampleModel` ed eseguire l'override del metodo `OnValueChanged` della classe annidata `DefaultNamespacePropertyHandler` di `ExampleModel` per chiamare `OnDefaultNamespaceChanged`.

Poiché la proprietà una proprietà DefaultNamespace viene utilizzata per calcolare la proprietà di rilevamento dello spazio dei nomi, `ExampleModel` necessario notificare a tutte `ExampleElement` classi di dominio che il valore di una proprietà DefaultNamespace è stato modificato.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Per modificare il gestore della proprietà rilevata

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

## <a name="add-custom-code-for-the-tracking-property"></a>Aggiungere codice personalizzato per la proprietà di rilevamento

Aggiungere un metodo di `CalculateNamespace` alla classe di dominio `ExampleElement`.

La definizione di questo metodo fornisce la logica per la proprietà calcolata CustomElements di `ExampleModel`. Questo metodo conta il numero di `ExampleElement` classi di dominio che dispongono di una proprietà di rilevamento dello spazio dei nomi che si trova nello stato aggiornato da utente e restituisce una stringa che rappresenta questo conteggio come una proporzione degli elementi totali del modello.

Aggiungere inoltre archiviazione per i metodi e per ottenere e impostare la proprietà archiviazione personalizzata dello spazio dei nomi della classe di dominio `ExampleElement`.

> [!NOTE]
> Il codice generato dagli strumenti DSL per `ExampleModel` chiama i metodi get e set; Tuttavia, gli strumenti DSL non generano il codice che implementa i metodi.

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

Aggiungere il codice per supportare il comportamento di post-caricamento personalizzato per la serializzazione XML.

> [!NOTE]
> Il codice generato dagli strumenti DSL chiama il `OnPostLoadModel` e `OnPostLoadModelAndDiagram` metodi; Tuttavia, gli strumenti DSL non generano codice che implementi questi metodi.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Per aggiungere il codice per supportare il comportamento di post-caricamento personalizzato

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

Il passaggio successivo consiste nel compilare ed eseguire la finestra di progettazione DSL in una nuova istanza di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] in modo che sia possibile verificare il corretto funzionamento della proprietà di rilevamento.

1. Nel menu **Compila** fare clic su **Ricompila soluzione**.

2. Scegliere **Avvia debug** dal menu **Debug**.

    La build sperimentale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] apre la soluzione di **debug** , che contiene un file di test vuoto.

3. In **Esplora soluzioni**fare doppio clic sul file test. TrackingPropertyDSL per aprirlo nella finestra di progettazione, quindi fare clic sull'area di progettazione.

    Si noti che nella finestra **Proprietà** del diagramma la proprietà **dello spazio dei nomi predefinita** è **una proprietà DefaultNamespace**e la proprietà **elementi personalizzati** è **0/0**.

4. Trascinare un elemento **ExampleElement** dalla **casella degli strumenti** alla superficie del diagramma.

5. Nella finestra **Proprietà** dell'elemento selezionare la proprietà **spazio dei nomi elemento** e modificare il valore da **una proprietà DefaultNamespace** a **otherNamespace**.

    Si noti che il valore dello **spazio dei nomi dell'elemento** è ora visualizzato in grassetto.

6. Nella finestra **Proprietà** fare clic con il pulsante destro del mouse su **spazio dei nomi elemento**, quindi scegliere **Reimposta**.

    Il valore della proprietà viene modificato in **una proprietà DefaultNamespace**e il valore viene visualizzato in un tipo di carattere normale.

    Fare nuovamente clic con il pulsante destro del mouse su **namespace elemento** Il comando **Reimposta** è ora disabilitato perché la proprietà si trova attualmente nello stato di rilevamento.

7. Trascinare un altro **esempio** di elemento dalla **casella degli strumenti** nella superficie del diagramma e modificare lo **spazio dei nomi dell'elemento** in **otherNamespace**.

8. Fare clic sull'area di progettazione.

    Nella finestra **Proprietà** del diagramma il valore degli **elementi personalizzati** è ora **1/2**.

9. Modificare **lo spazio dei nomi predefinito** per il diagramma da **una proprietà DefaultNamespace** a **newNamespace**.

     Lo **spazio dei nomi** del primo elemento tiene traccia della proprietà **predefinita dello spazio dei nomi** , mentre lo **spazio dei nomi** del secondo elemento mantiene il valore aggiornato dall'utente **otherNamespace**.

10. Salvare la soluzione e quindi chiudere la build sperimentale.

## <a name="next-steps"></a>Passaggi successivi

Se si prevede di utilizzare più di una proprietà di rilevamento o di implementare proprietà di rilevamento in più di un linguaggio DSL, è possibile creare un modello di testo per generare il codice comune per supportare ogni proprietà di rilevamento. Per ulteriori informazioni sui modelli di testo, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Procedura: Creare una soluzione per un linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md)
