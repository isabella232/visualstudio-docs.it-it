---
title: 'Procedura dettagliata: creare un progetto di definizione di sito di base | Microsoft Docs'
description: In questa procedura dettagliata di SharePoint, vedere come creare una definizione di sito di base contenente una Web part visiva con alcuni controlli.
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
ms.workload:
- office
ms.openlocfilehash: def1ae862a7b9ba4def62cb590260c5a18758929
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937706"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Procedura dettagliata: creare un progetto di definizione di sito di base
  In questa procedura dettagliata viene illustrato come creare una definizione di sito di base contenente una Web part visiva con alcuni controlli. Per maggiore chiarezza, la Web part visiva creata dispone solo di alcuni controlli. Tuttavia, è possibile creare definizioni di sito di SharePoint più sofisticate che includono più funzionalità.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di una definizione di sito tramite il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello di progetto.

- Creazione di un sito di SharePoint utilizzando una definizione di sito in SharePoint.

- Aggiunta di una Web part visiva alla soluzione.

- Personalizzazione della pagina default. aspx del sito aggiungendo la nuova Web part visiva.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint. Per ulteriori informazioni, vedere Requisiti per lo sviluppo di soluzioni SharePoint.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>Creare una soluzione di definizione del sito
 Per prima cosa, creare il progetto di definizione del sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>Per creare un progetto di definizione di sito

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**. Se l'IDE è configurato per usare Visual Basic impostazioni di sviluppo, sulla barra dei menu scegliere **file**  >  **nuovo progetto**.

    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Espandere il nodo **Visual C#** o il nodo **Visual Basic** , espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

3. Nell'elenco **modelli** scegliere il modello di **progetto SharePoint 2010** .

4. Nella casella **nome** immettere **TestSiteDef**, quindi scegliere il pulsante **OK** .

    Viene visualizzata la **personalizzazione guidata SharePoint** .

5. Nella pagina **specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il sito di SharePoint in cui si desidera eseguire il debug della definizione del sito oppure utilizzare il percorso predefinito (http://<em>System Name</em>/).

6. Nella sezione **Qual è il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm** .

    Tutti i progetti di definizione del sito devono essere distribuiti come soluzioni farm. Per ulteriori informazioni sulle soluzioni create mediante sandbox e sulle soluzioni farm, vedere Considerazioni sulle soluzioni [create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

7. Fare clic sul pulsante **Fine**.

    Il progetto viene visualizzato in **Esplora soluzioni**.

8. In **Esplora soluzioni** scegliere il nodo del progetto, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

9. In **Visual C#** o **Visual Basic** espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

10. Nel riquadro **modelli** scegliere il modello di **definizione del sito** , lasciare il **nome** **SiteDefinition1**, quindi scegliere il pulsante **Aggiungi** .

## <a name="create-a-visual-web-part"></a>Creare una Web part visiva
 Successivamente, creare una Web part visiva da visualizzare nella pagina principale della definizione del sito.

#### <a name="to-create-a-visual-web-part"></a>Per creare una Web part visiva

1. In **Esplora soluzioni** scegliere il pulsante **Mostra tutti i file** .

2. Scegliere il nodo del progetto **SiteDefinition1** , quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

3. Espandere il nodo **Visual C#** o il nodo **Visual Basic** , espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

4. Nell'elenco dei modelli scegliere il modello **Web part visiva** , il nome predefinito VisualWebPart1, quindi scegliere il pulsante **Aggiungi** .

     Verrà aperto il file *VisualWebPart1. ascx* .

5. Nella parte inferiore di *VisualWebPart1. ascx* aggiungere il markup seguente per aggiungere tre controlli al form: una casella di testo, un pulsante e un'etichetta:

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

6. In *VisualWebPart1. ascx* aprire il file *VisualWebPart1.ascx.cs* (per [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ) o *VisualWebPart1. ascx. vb* (per [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), quindi aggiungere il codice seguente:

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     Questo codice aggiunge la funzionalità per il clic del pulsante della web part.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Aggiungere la Web part visiva alla pagina ASPX predefinita
 Aggiungere quindi la Web part visiva alla pagina ASPX predefinita della definizione del sito.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Per aggiungere una Web part visiva alla pagina ASPX predefinita

1. Aprire la pagina default. aspx, quindi aggiungere la riga seguente sotto il `WebPartPages` Tag:

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Questa riga associa il nome MyWebPartControls alla web part e al relativo codice. Il parametro *namespace* corrisponde allo spazio dei nomi usato nel file di codice *VisualWebPart1. ascx* .

2. Dopo l' `</asp:Content>` elemento, sostituire l'intera `ContentPlaceHolderId="PlaceHolderMain"` sezione e il relativo contenuto con il codice seguente:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Questo codice crea un riferimento alla web part visiva creata in precedenza.

3. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **SiteDefinition1** , quindi scegliere **Imposta come elemento di avvio**.

## <a name="deploy-and-run-the-site-definition-solution"></a>Distribuire ed eseguire la soluzione di definizione del sito
 Successivamente, distribuire il progetto in SharePoint e quindi eseguire il progetto.

#### <a name="to-deploy-and-run-the-site-definition"></a>Per distribuire ed eseguire la definizione di sito

- Sulla barra dei menu scegliere **Compila**  >  **Distribuisci TestSiteDef**.

- Premere **F5**.

     Visual Studio compila il codice, aggiunge le funzionalità, inserisce tutti i file in un file di soluzione SharePoint (WSP) e distribuisce il file WSP in SharePoint Server. SharePoint installa quindi i file e quindi attiva le funzionalità.

## <a name="create-a-site-based-on-the-site-definition"></a>Creare un sito basato sulla definizione del sito
 Successivamente, creare un sito usando la nuova definizione del sito.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Per creare un sito utilizzando la definizione del sito

1. Nel sito di SharePoint viene visualizzata la pagina nuovo sito di SharePoint.

2. Nella sezione **titolo e descrizione** immettere il **nuovo sito** per il titolo e una descrizione del sito.

3. Nella sezione **Indirizzo sito Web** immettere **MyNewSite** nella casella **nome URL** .

4. Nella sezione **modello** scegliere la scheda **personalizzazioni di SharePoint** .

5. Nell'elenco **selezionare un modello** scegliere **SiteDefinition1**.

6. Lasciare invariati i valori predefiniti delle altre impostazioni, quindi scegliere il pulsante **Crea** .

     Verrà visualizzato il nuovo sito.

## <a name="test-the-new-site"></a>Testare il nuovo sito
 Successivamente, testare il nuovo sito per verificare se funziona correttamente.

#### <a name="to-test-the-new-site"></a>Per testare il nuovo sito

- Nella pagina default ASPX immettere il testo, quindi scegliere il pulsante **modifica testo etichetta** accanto alla casella di testo.

     Il testo viene visualizzato nell'etichetta sul lato destro del pulsante.

## <a name="see-also"></a>Vedi anche
- [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
