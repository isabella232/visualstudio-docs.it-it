---
title: Impostazione di un'immagine di sfondo in un diagramma
description: Si apprenderà che in Visual Studio Visualization and Modeling SDK è possibile impostare l'immagine di sfondo per una finestra di progettazione generata usando codice personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4de75e34696f7404488e804a87aa6f1d6c065860855e76b1ae1a7930f2940def
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231457"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Impostazione di un'immagine di sfondo in un diagramma
In Visual Studio Visualization and Modeling SDK è possibile impostare l'immagine di sfondo per una finestra di progettazione generata usando codice personalizzato.

## <a name="setting-the-background-image"></a>Impostazione dell'immagine di sfondo

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Per impostare un'immagine di sfondo per una finestra di progettazione generata

1. Copiare il file di immagine da usare come sfondo per il diagramma nella directory Dsl\Resources del progetto corrente.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla cartella Dsl\Resources, scegliere Aggiungi **e** quindi fare clic su **Elemento esistente.**

3. Nella finestra **di dialogo Aggiungi** elemento esistente passare alla cartella Dsl\Resources.

4. **Nell'elenco File di tipo fare** clic su File di **immagine**.

5. Fare clic sul file di immagine copiato nella directory e quindi fare clic su **Aggiungi**.

6. Fare clic con il pulsante destro del mouse su Dsl e **scegliere Proprietà** per aprire le proprietà del progetto Dsl.

7. Nella scheda **Risorse** fare clic su **Questo progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno.**

8. Aggiungere il file di immagine al file di risorse trascinando l'immagine **Esplora soluzioni** nella finestra delle risorse.

9. Aprire il menu File e fare clic sull'opzione per salvare le proprietà del progetto.

10. Verificare che il file Dsl\Properties\Resources.resx sia presente e contenga il file Resources.Designer.cs.

11. Se Resources.Designer.cs è mancante, fare clic sul file Resources.resx in **Esplora soluzioni**.

12. Nella finestra **Proprietà** impostare la proprietà `Custom Tool` su `ResXFileCodeGenerator`.

13. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto Dsl, scegliere Aggiungi **e** fare clic su **Nuova cartella.**

14. Assegnare alla cartella il **nome Custom.**

15. Fare clic con il pulsante destro del mouse sulla cartella Custom , **scegliere Aggiungi** e fare clic su **Nuovo elemento**.

16. **Nell'elenco Modelli** della finestra di dialogo Aggiungi nuovo **elemento** fare clic su File **di codice**.

17. Nella casella **Nome** digitare e `BackgroundImage.cs` fare clic su **Aggiungi**.

18. Copiare il codice seguente nel file BackgroundImage.cs, usando lo spazio dei nomi, il nome della classe del diagramma e il nome della risorsa del file di immagine corretti.

     Sostituire "MyDiagramClass" con il nome della classe parziale del diagramma definita in Dsl\GeneratedCode\Diagrams.cs. È anche possibile recuperare lo spazio dei nomi corretto dal file Dsl\GeneratedCode\Diagrams.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Per altre informazioni sulla personalizzazione del modello con il codice programma, vedere Esplorazione e aggiornamento [di un modello nel codice programma.](../modeling/navigating-and-updating-a-model-in-program-code.md)

## <a name="see-also"></a>Vedi anche

- [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)
- [Personalizzazione dei campi testo e immagine](../modeling/customizing-text-and-image-fields.md)
- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
