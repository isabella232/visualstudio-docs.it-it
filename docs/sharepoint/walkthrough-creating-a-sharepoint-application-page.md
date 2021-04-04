---
title: "Procedura dettagliata: creazione di una pagina dell'applicazione SharePoint | Microsoft Docs"
description: In questa procedura dettagliata creare una pagina dell'applicazione (un modulo specializzato di una pagina ASP.NET) e quindi eseguirne il debug tramite un sito di SharePoint locale.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6640373dac6d08144f1ef7fd230afa172540afe6
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217762"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Procedura dettagliata: creare una pagina dell'applicazione SharePoint

Una pagina dell'applicazione è un modulo specializzato di una pagina ASP.NET. Le pagine dell'applicazione contengono contenuto unito a una pagina master di SharePoint. Per ulteriori informazioni, vedere [creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

In questa procedura dettagliata viene illustrato come creare una pagina dell'applicazione ed eseguirne il debug tramite un sito di SharePoint locale. In questa pagina vengono visualizzati tutti gli elementi creati o modificati da ogni utente in tutti i siti del server farm.

Vengono illustrate le attività seguenti:

- Creazione di un progetto SharePoint.
- Aggiunta di una pagina dell'applicazione al progetto SharePoint.
- Aggiunta di controlli ASP.NET alla pagina dell'applicazione.
- Aggiunta di codice dietro i controlli ASP.NET.
- Test della pagina dell'applicazione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Windows e SharePoint.

## <a name="create-a-sharepoint-project"></a>Creazione di un progetto SharePoint

Per prima cosa, creare un **progetto SharePoint vuoto**. Successivamente, verrà aggiunto un elemento della **pagina dell'applicazione** al progetto.

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Aprire la finestra di dialogo **nuovo progetto** , espandere il nodo **Office/SharePoint** sotto la lingua che si desidera utilizzare, quindi scegliere il nodo **soluzioni di SharePoint** .

3. Nel riquadro **modelli Visual Studio installati** scegliere il modello di **progetto SharePoint 2010-vuoto** . Denominare il progetto **MySharePointProject**, quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** . Questa procedura guidata consente di selezionare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.

4. Scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **fine** per accettare il sito di SharePoint locale predefinito.

## <a name="create-an-application-page"></a>Creare una pagina dell'applicazione

Per creare una pagina dell'applicazione, aggiungere un elemento della **pagina dell'applicazione** al progetto.

1. In **Esplora soluzioni** scegliere il progetto **MySharePointProject** .

2. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere la **pagina applicazione (modello solo soluzione farm** .

4. Denominare la pagina **SearchItems**, quindi scegliere il pulsante **Aggiungi** .

     Nella finestra di progettazione di Visual Web Developer viene visualizzata la pagina dell'applicazione nella visualizzazione **origine** , in cui è possibile visualizzare gli elementi HTML della pagina. Nella finestra di progettazione viene visualizzato il markup per diversi <xref:System.Web.UI.WebControls.Content> controlli. Ogni controllo viene mappato a un <xref:System.Web.UI.WebControls.ContentPlaceHolder> controllo definito nella pagina master dell'applicazione predefinita.

## <a name="design-the-layout-of-the-application-page"></a>Progettare il layout della pagina dell'applicazione

L'elemento della pagina dell'applicazione consente di usare una finestra di progettazione per aggiungere controlli ASP.NET alla pagina dell'applicazione. Questa finestra di progettazione è la stessa utilizzata in Visual Web Developer. Aggiungere un'etichetta, un elenco di pulsanti di opzione e una tabella alla visualizzazione **origine** della finestra di progettazione e quindi impostare le proprietà come quando si progetta una pagina ASP.NET standard.

1. Sulla barra dei menu scegliere **Visualizza**  >  **casella degli strumenti**.

2. Nel nodo standard della **casella degli strumenti** eseguire uno dei passaggi seguenti:

    - Aprire il menu di scelta rapida per l'elemento **etichetta** , scegliere **copia**, aprire il menu di scelta rapida per la riga sotto il controllo contenuto **PlaceHolderMain** nella finestra di progettazione, quindi scegliere **Incolla**.

    - Trascinare l'elemento **Label** dalla **casella degli strumenti** nel corpo del controllo contenuto **PlaceHolderMain** .

3. Ripetere il passaggio precedente per aggiungere un elemento **DropDownList** e un elemento della **tabella** al controllo contenuto **PlaceHolderMain** .

4. Nella finestra di progettazione modificare il valore dell' `Text` attributo del controllo etichetta in modo da **visualizzare tutti gli elementi**.

5. Nella finestra di progettazione sostituire l' `<asp:DropDownList>` elemento con il codice XML seguente.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Gestire gli eventi dei controlli nella pagina

Gestire i controlli in una pagina dell'applicazione in modo analogo a qualsiasi pagina ASP.NET. In questa procedura verrà gestito l' `SelectedIndexChanged` evento dell'elenco a discesa.

1. Scegliere **codice** dal menu **Visualizza** .

     Il file di codice della pagina dell'applicazione verrà aperto nell'editor di codice.

2. Aggiungi alla classe `SearchItems` il metodo seguente. Questo codice gestisce l' <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> evento di chiamando <xref:System.Web.UI.WebControls.DropDownList> un metodo che verrà creato più avanti in questa procedura dettagliata.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet5":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet5":::

3. Aggiungere le seguenti istruzioni all'inizio del file di codice della pagina dell'applicazione.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet1":::

4. Aggiungi alla classe `SearchItems` il metodo seguente. Questo metodo scorre tutti i siti nella server farm e cerca gli elementi creati o modificati dall'utente corrente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet2":::

5. Aggiungi alla classe `SearchItems` il metodo seguente. Questo metodo consente di visualizzare gli elementi creati o modificati dall'utente corrente nella tabella.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet3":::

## <a name="test-the-application-page"></a>Testare la pagina dell'applicazione

Quando si esegue il progetto, viene aperto il sito di SharePoint e viene visualizzata la pagina applicazione.

1. In **Esplora soluzioni** aprire il menu di scelta rapida per la pagina applicazione, quindi scegliere **Imposta come elemento di avvio**.

2. Premere **F5**.

     Verrà aperto il sito di SharePoint.

3. Nella pagina applicazione scegliere l'opzione **modificato da me** .

     La pagina dell'applicazione viene aggiornata e vengono visualizzati tutti gli elementi modificati in tutti i siti del server farm.

4. Nella pagina applicazione scegliere **creato dall'** utente nell'elenco.

     La pagina dell'applicazione viene aggiornata e vengono visualizzati tutti gli elementi creati in tutti i siti del server farm.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sulle pagine dell'applicazione SharePoint, vedere [creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Per ulteriori informazioni su come progettare il contenuto di una pagina di SharePoint utilizzando la finestra di progettazione Web visiva, vedere gli argomenti seguenti:

- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Creazione di controlli riutilizzabili per Web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Vedi anche

[Procedura: creare una pagina](../sharepoint/how-to-create-an-application-page.md) 
 dell'applicazione [Tipo di pagina _layouts applicazione](/previous-versions/office/aa979604(v=office.14))
