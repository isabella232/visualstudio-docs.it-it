---
title: 'Procedura dettagliata: Creare una definizione di sito di base Project | Microsoft Docs'
description: In questa SharePoint procedura dettagliata, vedere come creare una definizione di sito di base che contiene una web part visiva con alcuni controlli.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2d8de9b5da1a9bff70b8332b9b6804295996af5e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130806"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Procedura dettagliata: Creare un progetto di definizione del sito di base
  Questa procedura dettagliata illustra come creare una definizione di sito di base che contiene una web part visiva con alcuni controlli. Per maggiore chiarezza, la web part visiva creata include solo alcuni controlli. Tuttavia, è possibile creare definizioni di sito SharePoint più sofisticate che includono più funzionalità.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di una definizione di sito tramite il modello [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di progetto.

- Creazione di SharePoint sito usando una definizione di sito in SharePoint.

- Aggiunta di una web part visiva alla soluzione.

- Personalizzazione della pagina default.aspx del sito aggiungendo la nuova web part visiva.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint. Per altre informazioni, vedere Requisiti per lo sviluppo SharePoint soluzioni.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>Creare una soluzione di definizione del sito
 Creare prima di tutto il progetto di definizione del sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>Per creare un progetto di definizione del sito

1. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project**. Se l'IDE è impostato per l'Visual Basic di sviluppo, sulla barra dei menu scegliere **Nuovo**  >  **file Project**.

    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Espandere il **nodo Visual C#** o **Visual Basic,**  espandere il nodo SharePoint e quindi scegliere il **nodo 2010.**

3. **Nell'elenco** Modelli scegliere il **modello SharePoint 2010 Project** 2010.

4. Nella casella **Nome** immettere **TestSiteDef** e quindi scegliere **il pulsante OK.**

    Verrà **visualizzata SharePoint personalizzazione** guidata.

5. Nella  pagina Specificare il sito e il livello di sicurezza per il debug immettere l'URL per il sito di SharePoint in cui si vuole eseguire il debug della definizione del sito o usare il percorso predefinito (http://<em>Nome</em>sistema /).

6. Nella sezione **Qual è il livello di attendibilità** per SharePoint soluzione? scegliere il pulsante **di** opzione Distribuisci come soluzione farm.

    Tutti i progetti di definizione del sito devono essere distribuiti come soluzioni farm. Per altre informazioni sulle soluzioni sandbox rispetto alle soluzioni farm, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

7. Fare clic sul pulsante **Fine**.

    Il progetto viene visualizzato in **Esplora soluzioni**.

8. In **Esplora soluzioni** scegliere il nodo del progetto e quindi nella barra dei menu **scegliere** Project Aggiungi  >  **nuovo elemento.**

9. In **Visual C#** o **Visual Basic** espandere  il SharePoint e quindi scegliere il **nodo 2010.**

10. Nel riquadro **Modelli** scegliere il modello Definizione  **sito,** lasciare **SiteDefinition1** come Nome e quindi scegliere il **pulsante** Aggiungi.

## <a name="create-a-visual-web-part"></a>Creare una web part visiva
 Creare quindi una web part visiva da visualizzare nella pagina principale della definizione del sito.

#### <a name="to-create-a-visual-web-part"></a>Per creare una web part visiva

1. In **Esplora soluzioni** scegliere il **pulsante Mostra tutti i** file.

2. Scegliere il **nodo del progetto SiteDefinition1** e quindi nella barra dei menu **scegliere** Project Aggiungi  >  **nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

3. Espandere il **nodo Visual C#** o **Visual Basic,**  espandere il nodo SharePoint e quindi scegliere il **nodo 2010.**

4. Nell'elenco dei modelli scegliere il **modello Web part** visuale, mantenere il nome predefinito VisualWebPart1 e quindi scegliere il **pulsante** Aggiungi.

     Verrà aperto il file *VisualWebPart1.ascx.*

5. Nella parte inferiore di *VisualWebPart1.ascx* aggiungere il markup seguente per aggiungere tre controlli al form: una casella di testo, un pulsante e un'etichetta:

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. In *VisualWebPart1.ascx* aprire il file *VisualWebPart1.ascx.cs* (per ) o [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] *VisualWebPart1.ascx.vb* (per ) e quindi aggiungere il [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] codice seguente:

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

     Questo codice aggiunge funzionalità per il clic sul pulsante della web part.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Aggiungere la web part visiva alla pagina ASPX predefinita
 Aggiungere quindi la web part visiva alla pagina ASPX predefinita della definizione del sito.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Per aggiungere una web part visiva alla pagina ASPX predefinita

1. Aprire la pagina default.aspx e quindi aggiungere la riga seguente sotto il `WebPartPages` tag :

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Questa riga associa il nome MyWebPartControls alla web part e al relativo codice. Il *parametro Namespace* corrisponde allo spazio dei nomi usato nel file di codice *VisualWebPart1.ascx.*

2. Dopo `</asp:Content>` l'elemento , sostituire `ContentPlaceHolderId="PlaceHolderMain"` l'intera sezione e il relativo contenuto con il codice seguente:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Questo codice crea un riferimento alla web part visiva creata in precedenza.

3. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **SiteDefinition1** e quindi scegliere **Imposta come elemento di avvio.**

## <a name="deploy-and-run-the-site-definition-solution"></a>Distribuire ed eseguire la soluzione di definizione del sito
 Distribuire quindi il progetto in SharePoint e quindi eseguire il progetto.

#### <a name="to-deploy-and-run-the-site-definition"></a>Per distribuire ed eseguire la definizione di sito

- Sulla barra dei menu scegliere **Compila**  >  **Distribuisci TestSiteDef**.

- Premere **F5**.

     Visual Studio compila il codice, ne aggiunge le funzionalità, inserisce tutti i file in un file della soluzione SharePoint (WSP) e distribuisce il file WSP in SharePoint Server. SharePoint quindi installa i file e quindi attiva le funzionalità.

## <a name="create-a-site-based-on-the-site-definition"></a>Creare un sito in base alla definizione del sito
 Creare quindi un sito usando la nuova definizione di sito.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Per creare un sito usando la definizione del sito

1. Nel sito SharePoint viene visualizzata la pagina SharePoint sito.

2. Nella sezione **Titolo e descrizione** immettere **My New Site** come titolo e una descrizione del sito.

3. Nella sezione **Indirizzo sito Web** immettere **mynewsite** nella casella **Nome URL.**

4. Nella sezione **Modello** scegliere la SharePoint **Personalizzazioni.**

5. **Nell'elenco Selezionare un** modello scegliere **SiteDefinition1.**

6. Lasciare i valori predefiniti per le altre impostazioni e quindi scegliere **il pulsante** Crea.

     Verrà visualizzato il nuovo sito.

## <a name="test-the-new-site"></a>Testare il nuovo sito
 Testare quindi il nuovo sito per verificare se funziona correttamente.

#### <a name="to-test-the-new-site"></a>Per testare il nuovo sito

- Nella pagina ASPX predefinita immettere del testo e quindi scegliere il pulsante **Cambia** testo etichetta accanto alla casella di testo.

     Il testo viene visualizzato nell'etichetta sul lato destro del pulsante.

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
