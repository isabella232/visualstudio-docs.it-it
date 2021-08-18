---
title: Incorporamento di un diagramma in Windows Form
description: Informazioni su come incorporare un diagramma DSL in un controllo Windows, visualizzato nella finestra Visual Studio dati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: f7c8abdb8b3eff82c7dc36ec9be8bb7e9c1be7d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150573"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Incorporare un diagramma in Windows Form

È possibile incorporare un diagramma DSL in Windows, che viene visualizzato nella finestra Visual Studio.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Incorporare un diagramma DSL in un controllo Windows dati

1. Aggiungere un nuovo file **di controllo** utente al progetto DslPackage.

2. Aggiungere un controllo Panel al controllo utente. Questo pannello conterrà il diagramma DSL.

     Aggiungere altri controlli necessari.

     Impostare le proprietà Di ancoraggio dei controlli.

3. In Esplora soluzioni fare clic con il pulsante destro del mouse sul file del controllo utente e scegliere **Visualizza codice**. Aggiungere questo costruttore e la variabile al codice:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Aggiungere un nuovo file al progetto DslPackage con il contenuto seguente:

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. Per testare il DSL, premere **F5** e aprire un file di modello di esempio. Il diagramma viene visualizzato all'interno del controllo . La casella degli strumenti e altre funzionalità funzionano normalmente.

## <a name="update-the-form-using-store-events"></a>Aggiornare il modulo usando gli eventi dell'archivio

1. Nella finestra di progettazione form aggiungere un **controllo ListBox** denominato `listBox1` . Verrà visualizzato un elenco degli elementi nel modello. Viene sincronizzato con il modello usando gli *eventi dell'archivio*. Per altre informazioni, vedere [Gestori eventi Propagare le modifiche all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Nel file di codice personalizzato eseguire l'override di altri metodi per la classe DocView:

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. Nel code-behind del controllo utente inserire i metodi per restare in ascolto degli elementi aggiunti e rimossi:

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. Per testare il DSL, premere **F5** e nell'istanza sperimentale di Visual Studio aprire un file di modello di esempio.

     Si noti che la casella di riepilogo mostra un elenco degli elementi nel modello e che è corretto dopo qualsiasi aggiunta o eliminazione e dopo Undo e Redo.

## <a name="see-also"></a>Vedi anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
