---
title: 'Procedura dettagliata: Creare un progetto di definizione sito di base | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8a9a879db7c1d24dbfd8312dbc75d9b0bbaa8803
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844416"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Procedura dettagliata: Creare un progetto di definizione sito di base
  Questa procedura dettagliata illustra come creare una definizione di sito di base che contiene una Web part visiva con alcuni controlli su di esso. Per chiarezza, la Web part visiva che creano include solo alcuni controlli. Tuttavia, è possibile creare definizioni di sito di SharePoint più sofisticate che includono più funzionalità.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
- Creazione di una definizione di sito tramite il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello di progetto.  
  
- Creazione di un sito di SharePoint usando una definizione di sito in SharePoint.  
  
- Aggiunta di una Web part visiva alla soluzione.  
  
- Personalizzazione pagina default. aspx del sito mediante l'aggiunta la nuova Web part visiva.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint. Per altre informazioni, vedere i requisiti per lo sviluppo di soluzioni di SharePoint.  
  
-   Visual Studio.  
  
## <a name="create-a-site-definition-solution"></a>Creare una soluzione di definizione sito
 In primo luogo, creare il progetto di definizione sito nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Per creare un progetto di definizione sito  
  
1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**. Se l'IDE è configurato per usare le impostazioni di sviluppo di Visual Basic, nella barra dei menu, scegliere **File** > **nuovo progetto**.  
  
    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2. Espandere la **Visual c#** nodo o il **Visual Basic** nodo, espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
3. Nel **modelli** scegliere i **progetto SharePoint 2010** modello.  
  
4. Nel **Name** casella, immettere **TestSiteDef**e quindi scegliere il **OK** pulsante.  
  
    Il **Personalizzazione guidata SharePoint** viene visualizzata.  
  
5. Nel **specificare il livello di sito e la sicurezza per il debug** pagina, immettere l'URL per il sito di SharePoint in cui si desidera eseguire il debug della definizione di sito o utilizzare il percorso predefinito (http://<em>il nome del sistema</em>/).  
  
6. Nel **qual è il livello di attendibilità per la soluzione SharePoint?** keychains le **Distribuisci come soluzione farm** pulsante di opzione.  
  
    Tutti i progetti di definizione sito devono essere distribuiti come soluzioni farm. Per altre informazioni sulle soluzioni create mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Scegliere il **fine** pulsante.  
  
    Il progetto viene visualizzato nella **Esplora soluzioni**.  
  
8. Nelle **Esplora soluzioni**, scegliere il nodo del progetto e quindi nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento**.  
  
9. In presenza di una **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
10. Nel **modelli** riquadro, scegliere il **definizione sito** modello, lasciare il **nome** come **SiteDefinition1**e quindi scegliere il  **Aggiungere** pulsante.  
  
## <a name="create-a-visual-web-part"></a>Creare una web part visiva
 Successivamente, creare una Web part visiva deve essere visualizzato nella pagina principale della definizione di sito.  
  
#### <a name="to-create-a-visual-web-part"></a>Per creare una web part visiva
  
1.  Nelle **Esplora soluzioni**, scegliere il **Mostra tutti i file** pulsante.  
  
2.  Scegliere il **SiteDefinition1** nodo di progetto e quindi nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Espandere la **Visual c#** nodo o il **Visual Basic** nodo, espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
4.  Nell'elenco dei modelli, scegliere il **Web Part visiva** modello, mantenere il valore predefinito nome VisualWebPart1 e quindi scegliere il **Add** pulsante.  
  
     Il *VisualWebPart1.ascx* file viene aperto.  
  
5.  In fondo *VisualWebPart1.ascx*, aggiungere il markup seguente per aggiungere tre controlli al form: una casella di testo, un pulsante e un'etichetta:  
  
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
  
6.  Sotto *VisualWebPart1.ascx*, aprire il *VisualWebPart1.ascx.cs* file (per [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) oppure *VisualWebPart1.ascx.vb* (per [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), quindi aggiungere il codice seguente:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Questo codice aggiunge funzionalità per clic del pulsante della web part.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Aggiungere la web part visiva alla pagina ASPX predefinita
 Successivamente, aggiungere la Web part visiva alla pagina ASPX predefinita della definizione di sito.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Per aggiungere una web part visiva alla pagina ASPX predefinita
  
1.  Aprire la pagina default. aspx e quindi aggiungere la riga seguente sotto il `WebPartPages` tag:  
  
    ```aspx-csharp  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Questa riga associa il nome MyWebPartControls con la Web part e il relativo codice. Il *Namespace* parametro corrisponda a spazio dei nomi che viene utilizzata per il *VisualWebPart1.ascx* file di codice.  
  
2.  Dopo il `</asp:Content>` elemento, sostituire l'intero `ContentPlaceHolderId="PlaceHolderMain"` sezione e il relativo contenuto con il codice seguente:  
  
    ```aspx-csharp  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Questo codice crea un riferimento per la Web part visiva creata in precedenza.  
  
3.  Nel **Esplora soluzioni**, aprire il menu di scelta rapida per il **SiteDefinition1** nodo, quindi scegliere **imposta come elemento di avvio**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Distribuire ed eseguire la soluzione di definizione sito
 Successivamente, distribuire il progetto in SharePoint e quindi eseguire il progetto.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Per distribuire ed eseguire la definizione di sito  
  
-   Nella barra dei menu, scegliere **compilare** > **distribuire TestSiteDef**.  
  
-   Premere **F5**.  
  
     Visual Studio compila il codice aggiunge le relative funzionalità, inclusi tutti i file in un file di soluzione (WSP) di SharePoint e consente di distribuire il file WSP nel SharePoint Server. SharePoint installa quindi i file e quindi attiva le funzionalità.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Creare un sito basato sulla definizione di sito
 Successivamente, creare un sito usando la nuova definizione sito.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Per creare un sito usando la definizione di sito  
  
1.  Nel sito di SharePoint, viene visualizzata la pagina nuovo sito di SharePoint.  
  
2.  Nel **Title e Description** , quindi immettere **risorse del nuovo sito** per il titolo e una descrizione del sito.  
  
3.  Nel **indirizzo del sito Web** , quindi immettere **NuovoSito** nel **nome URL** casella.  
  
4.  Nel **modello** keychains le **personalizzazioni di SharePoint** scheda.  
  
5.  Nel **selezionare un modello** casella di riepilogo **SiteDefinition1**.  
  
6.  Lasciare le altre impostazioni sui valori predefiniti e quindi scegliere il **Create** pulsante.  
  
     Viene visualizzato il nuovo sito.  
  
## <a name="test-the-new-site"></a>Testare il nuovo sito
 Testare quindi il nuovo sito per verificare se funziona correttamente.  
  
#### <a name="to-test-the-new-site"></a>Per testare il nuovo sito  
  
-   Nella pagina ASPX predefinita, immettere il testo e quindi scegliere il **testo dell'etichetta Cambia** pulsante accanto alla casella di testo.  
  
     Il testo viene visualizzato nell'etichetta a destra del pulsante.  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
