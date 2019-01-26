---
title: 'Procedura dettagliata: Creazione di una pagina di applicazione di SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 802c20a21b624e868cddac4badfd8827ef765506
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866191"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Procedura dettagliata: Creare una pagina dell'applicazione SharePoint
 
Una pagina dell'applicazione è un tipo speciale di una pagina ASP.NET. Le pagine dell'applicazione includono contenuto che viene unito a una pagina master di SharePoint. Per altre informazioni, vedere [creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Questa procedura dettagliata illustra come creare una pagina dell'applicazione e quindi eseguirne il debug tramite un sito di SharePoint locale. Questa pagina Mostra tutti gli elementi di ogni utente ha creato o modificato in tutti i siti nella server farm.

Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un progetto SharePoint.
- Aggiunta di una pagina dell'applicazione al progetto SharePoint.
- Aggiunta di controlli ASP.NET alla pagina dell'applicazione.
- Aggiunta di code-behind i controlli ASP.NET.
- Test della pagina dell'applicazione.

> [!NOTE]
> I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Windows e SharePoint.

## <a name="create-a-sharepoint-project"></a>Creare un progetto SharePoint

Creare prima di tutto una **progetto SharePoint vuoto**. In seguito aggiungerà un' **pagina dell'applicazione** elemento al progetto.

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Aprire il **nuovo progetto** finestra di dialogo espandere il **Office/SharePoint** nodo sotto il linguaggio che si desidera usare e quindi scegliere il **soluzioni SharePoint** nodo.

3. Nel **modelli di Visual Studio installata** riquadro, scegliere il **SharePoint 2010 - progetto vuoto** modello. Denominare il progetto **MySharePointProject**, quindi scegliere il **OK** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzata. Questa procedura guidata consente di selezionare il sito che si utilizzerà per eseguire il debug del progetto e il livello di attendibilità della soluzione.

4. Scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di SharePoint locale predefinito.

## <a name="create-an-application-page"></a>Creare una pagina applicazione

Per creare una pagina applicazione, aggiungere un' **pagina dell'applicazione** elemento al progetto.

1. Nelle **Esplora soluzioni**, scegliere il **MySharePointProject** progetto.

2. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

3. Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **pagina dell'applicazione (solo soluzione Farm** modello.

4. Denominare la pagina **SearchItems**, quindi scegliere il **Add** pulsante.

     La finestra di progettazione di Visual Web Developer consente di visualizzare la pagina dell'applicazione in **origine** vista in cui è possibile visualizzare gli elementi HTML della pagina. La finestra di progettazione viene visualizzato il markup per diversi <xref:System.Web.UI.WebControls.Content> controlli. Ogni controllo è associato a un <xref:System.Web.UI.WebControls.ContentPlaceHolder> controllo definito nella pagina master dell'applicazione predefinito.

## <a name="design-the-layout-of-the-application-page"></a>Progettare il layout della pagina dell'applicazione

L'elemento pagina applicazione consente di usare una finestra di progettazione per aggiungere i controlli ASP.NET alla pagina dell'applicazione. Questa finestra di progettazione è la stessa finestra di progettazione utilizzato in Visual Web Developer. Aggiungere un'etichetta, un elenco di pulsanti di opzione e una tabella per la **origine** visualizzazione della finestra di progettazione e quindi impostare le proprietà come si farebbe quando si progetta di qualsiasi pagina ASP.NET standard.

1. Scegliere **Visualizza** > **Casella degli strumenti** sulla barra dei menu.

2. Nel nodo Standard della **casella degli strumenti**, effettuare una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il **Label** voce, scegliere **copia**, aprire il menu di scelta rapida per la riga sotto il **PlaceHolderMain** controllo nella finestra di progettazione, contenuto e quindi Scegli **Incolla**.

    - Trascinare il **etichetta** articolo dalle **della casella degli strumenti** nel corpo del **PlaceHolderMain** controllo contenuto.

3. Ripetere il passaggio precedente per aggiungere un **DropDownList** elemento e un **tabella** elemento per il **PlaceHolderMain** controllo contenuto.

4. Nella finestra di progettazione, modificare il valore della `Text` attributo del controllo etichetta **Mostra tutti gli elementi**.

5. Nella finestra di progettazione, sostituire il `<asp:DropDownList>` elemento con il codice XML seguente.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Gestire gli eventi dei controlli nella pagina

Gestire i controlli in una pagina dell'applicazione esattamente come si farebbe qualsiasi pagina ASP.NET. In questa procedura verrà gestito il `SelectedIndexChanged` evento dell'elenco di riepilogo a discesa.

1. Nel **View** menu, scegliere **codice**.

     File di codice della pagina applicazione verrà aperto nell'Editor del codice.

2. Aggiungere il metodo seguente alla classe `SearchItems` . Questo codice gestisce il <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> eventi del <xref:System.Web.UI.WebControls.DropDownList> chiamando un metodo che verrà creato più avanti in questa procedura dettagliata.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Aggiungere le istruzioni seguenti all'inizio del file di codice della pagina dell'applicazione.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Aggiungere il metodo seguente alla classe `SearchItems` . Questo metodo scorre tutti i siti nella server farm e ricerca gli elementi creati o modificati dall'utente corrente.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Aggiungere il metodo seguente alla classe `SearchItems` . Questo metodo consente di visualizzare gli elementi creati o modificati dall'utente corrente nella tabella.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Testare la pagina dell'applicazione

Quando si esegue il progetto, viene aperto il sito di SharePoint e viene visualizzata la pagina dell'applicazione.

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per la pagina dell'applicazione e quindi scegliere **imposta come elemento di avvio**.

2. Premere **F5**.

     Viene aperto il sito di SharePoint.

3. Nella pagina dell'applicazione, scegliere il **modificato da me** opzione.

     La pagina dell'applicazione viene aggiornata e visualizza tutti gli elementi che è stato modificato in tutti i siti nella server farm.

4. Nella pagina dell'applicazione, scegliere **creati da me** nell'elenco.

     La pagina dell'applicazione viene aggiornata e visualizza tutti gli elementi che è stato creato in tutti i siti nella server farm.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulle pagine dell'applicazione SharePoint, vedere [creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Ulteriori informazioni su come progettare contenuto pagina di SharePoint tramite Visual Web Designer da questi argomenti:

- [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Vedere anche

[Procedura: Creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)  
[Tipo di pagina applicazione layouts](http://go.microsoft.com/fwlink/?LinkID=169274)
