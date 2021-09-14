---
title: Come creare e applicare una risorsa
description: Informazioni su come creare e applicare una risorsa nel finestra di progettazione XAML in modo da poter archiviare e riutilizzare stili e modelli per gli elementi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: 556cf3fd25c7e629724ed2b1bad9bef0128abc6a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710548"
---
# <a name="how-to-create-and-apply-a-resource"></a>Come creare e applicare una risorsa

Stili e modelli per gli elementi nella finestra di progettazione XAML vengono archiviati in entità riutilizzabili dette risorse. Gli stili consentono di impostare le proprietà degli elementi e riutilizzare tali impostazioni per conferire un aspetto uniforme a più elementi. Un oggetto [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate) definisce l'aspetto di un controllo e può anche essere applicato come risorsa. Per altre informazioni, vedere [Stili XAML](/windows/uwp/design/controls-and-patterns/xaml-styles) e [Modelli di controllo](/windows/uwp/design/controls-and-patterns/control-templates).

Quando si crea una nuova risorsa da una proprietà, una classe [Style](xref:Windows.UI.Xaml.Style) o un oggetto [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate) esistente, la finestra di dialogo **Crea risorsa** consente di definire la risorsa a livello di applicazione, di documento o di elemento. Questi livelli determinano le posizioni in cui è possibile usare la risorsa. Se, ad esempio, si definisce la risorsa a livello di elemento, questa può essere applicata solo all'elemento in cui è stata creata. È anche possibile scegliere di archiviare la risorsa in un [dizionario risorse](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references), ovvero un file separato che è possibile riutilizzare in un altro progetto.

## <a name="create-a-new-resource"></a>Creare una nuova risorsa

1. Con un file XAML aperto nella finestra di progettazione XAML, creare un elemento oppure scegliere un elemento nella finestra Struttura documento.

2. Nella finestra **Proprietà** scegliere il marcatore della proprietà, rappresentato da un simbolo di casella a destra del valore di una proprietà e quindi scegliere **Converti in nuova risorsa**. Un simbolo di casella bianca indica un valore predefinito, mentre un simbolo di casella nera indica in genere che è stata applicata una risorsa locale.

     Verrà visualizzata la finestra di dialogo appropriata per la creazione di una risorsa. Questa finestra di dialogo viene visualizzata quando si crea una risorsa da un pennello:

     ![Finestra di dialogo Crea risorsa](../designers/media/xaml_create_resource.png)

3. Nella casella **Nome (chiave)** immettere un nome di chiave. Si tratta del nome che è possibile usare quando si vuole che altri elementi facciano riferimento alla risorsa.

4. In **Posizione definizione** scegliere l'opzione che specifica dove si vuole definire la risorsa:

    - Per rendere disponibile la risorsa per qualsiasi documento nell'applicazione, scegliere **Applicazione**.

    - Per rendere disponibile la risorsa solo per il documento corrente, scegliere **Documento corrente**.

    - Per rendere disponibile la risorsa solo per l'elemento da cui è stata creata o per i relativi elementi figlio, scegliere **Documento corrente** e nell'elenco a discesa selezionare **elemento**: **nome**.

    - Per definire la risorsa in un file di [dizionario risorse](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references) che può essere riutilizzato in altri progetti, fare clic su **Dizionario risorse**. Selezionare quindi un file di dizionario risorse esistente, ad esempio **StandardStyles.xaml**, nell'elenco a discesa.

5. Scegliere **OK** per creare la risorsa e applicarla all'elemento da cui è stata creata.

## <a name="apply-a-resource-to-an-element-or-property"></a>Applicare una risorsa a un elemento o a una proprietà

1. Nella finestra Struttura documento scegliere l'elemento a cui si vuole applicare una risorsa.

2. Eseguire una delle operazioni seguenti:

   - Applicare una risorsa a una proprietà. Nella finestra **Proprietà** scegliere l'indicatore di proprietà  accanto al valore della proprietà, scegliere Risorsa locale o Risorsa di sistema **e** quindi scegliere una risorsa disponibile nell'elenco visualizzato.

      Se non viene visualizzata una risorsa prevista, è possibile che il tipo della risorsa non corrisponda al tipo della proprietà.

   - Applicare uno stile o una risorsa modello di controllo a un controllo. Aprire il menu di scelta rapida per un controllo nella finestra Struttura documento, scegliere **Modifica modello** o **Modifica modelli aggiuntivi**, quindi scegliere **Applica risorsa** e infine selezionare il nome del modello di controllo nell'elenco visualizzato.

     > [!NOTE]
     > **Modifica modello** applica i modelli di controllo. L'opzione **Edit Additional Templates** (Modifica modelli aggiuntivi) consente di applicare altri tipi di modelli.

     Le risorse possono essere applicate ovunque siano compatibili. Ad esempio, una risorsa pennello può essere applicata alla proprietà **Foreground** di un controllo [TextBox](xref:Windows.UI.Xaml.Controls.TextBox).

## <a name="edit-a-resource"></a>Modificare una risorsa

1. Scegliere un elemento nella tavola da disegno o nella finestra Struttura documento.

2. Scegliere il marcatore della proprietà predefinito o locale a destra della proprietà nella finestra **Proprietà** e quindi scegliere **Modifica risorsa** per aprire la finestra di dialogo **Modifica risorsa**.

3. Modificare le opzioni per la risorsa.

## <a name="see-also"></a>Vedi anche

- [Creazione di un'interfaccia utente tramite XAML Designer](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
