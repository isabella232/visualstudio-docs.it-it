---
title: Incorporamento di un diagramma in un Windows Form | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 487105350fe5c62a9451bccc5713c6506c76bf1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669696"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Incorporamento di un diagramma in Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile incorporare un diagramma DSL in un controllo Windows, che viene visualizzato nella [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] finestra.

## <a name="embedding-a-diagram"></a>Incorporamento di un diagramma

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Per incorporare un diagramma DSL in un controllo Windows

1. Aggiungere un nuovo file di **controllo utente** al progetto DslPackage.

2. Aggiungere un controllo Panel al controllo utente. Questo pannello conterrà il diagramma DSL.

     Aggiungere altri controlli richiesti.

     Impostare le proprietà di ancoraggio dei controlli.

3. In Esplora soluzioni fare clic con il pulsante destro del mouse sul file di controllo utente e scegliere **Visualizza codice**. Aggiungere il costruttore e la variabile al codice:

    ```csharp

    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDSLDocView docView;

    ```

4. Aggiungere un nuovo file al progetto DslPackage con il contenuto seguente:

    ```
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

5. Per testare il linguaggio DSL, premere F5 e aprire un file di modello di esempio. Il diagramma viene visualizzato all'interno del controllo. La casella degli strumenti e altre funzionalità funzionano normalmente.

#### <a name="updating-the-form-using-store-events"></a>Aggiornamento del modulo tramite gli eventi di archiviazione

1. Nella finestra di progettazione del form aggiungere una **casella di riepilogo** denominata `listBox1` . Verrà visualizzato un elenco degli elementi nel modello. Verrà mantenuta in sincronia con il modello utilizzando *gli eventi di archiviazione*. Per ulteriori informazioni, vedere [i gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Nel file di codice personalizzato, eseguire l'override di altri metodi per la classe DocView:

    ```

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

3. Nel codice sottostante il controllo utente inserire i metodi per ascoltare gli elementi aggiunti e rimossi:

    ```

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

4. Per testare il linguaggio DSL, premere F5 e nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aprire un file di modello di esempio.

     Si noti che la casella di riepilogo Mostra un elenco degli elementi nel modello e che è corretta dopo qualsiasi aggiunta o eliminazione e dopo l'annullamento e il rollforward.

## <a name="see-also"></a>Vedere anche
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md) [scrittura di codice per personalizzare un Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md)
