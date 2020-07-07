---
title: 'Procedura: localizzare il markup ASPX | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63bd8ee614a78752069002820689a2cc6c0be783
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016288"
---
# <a name="how-to-localize-aspx-markup"></a>Procedura: localizzare il markup ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]le pagine (aspx) utilizzano in genere valori stringa hardcoded. Per localizzare queste stringhe, sostituirle con espressioni che fanno riferimento a risorse localizzate.

## <a name="localize-aspx-markup"></a>Localizzare il markup ASPX

#### <a name="to-localize-aspx-markup"></a>Per localizzare il markup ASPX

1. Aggiungere file di risorse separati: uno per la lingua predefinita e uno per ogni lingua localizzata.

     Se si localizzano solo markup e non codice, aggiungere un elemento di progetto file di risorse globali. Se si sta localizzando codice e markup, aggiungere un elemento di progetto file di risorse.

    1. Per aggiungere un file di risorse globale, in **Esplora soluzioni**aprire il menu di scelta rapida per un elemento del progetto SharePoint, quindi scegliere **Aggiungi**  >  **nuovo elemento**. Nel nodo SharePoint **2010** scegliere il modello **file di risorse globali** .

    2. Per aggiungere un file di risorse, in **Esplora soluzioni**aprire il menu di scelta rapida per un elemento del progetto SharePoint, quindi scegliere **Aggiungi**  >  **nuovo elemento**. Nel nodo **Visual Basic** o **Visual C#** scegliere il modello file di **risorse** .

    > [!NOTE]
    > Assicurarsi di aggiungere i file di risorse a un elemento del progetto SharePoint per abilitare la proprietà del tipo di distribuzione. Questa proprietà è obbligatoria più avanti in questa procedura. Se la soluzione non dispone di un elemento di progetto SharePoint, è possibile aggiungere un progetto SharePoint vuoto e rimuovere il file *Elements.xml* predefinito.

2. Assegnare al file di risorse della lingua predefinita un nome a scelta aggiunto con un'estensione *resx* , ad esempio MyAppResources. resx. Utilizzare lo stesso nome base per ogni file di risorse localizzato, ma aggiungere l'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] delle impostazioni cultura. Ad esempio, assegnare un nome a una risorsa localizzata in tedesco *MyAppResources.de-de. resx*.

3. Modificare il valore della proprietà **tipo distribuzione** di ogni file di risorse in **AppGlobalResource** per fare in modo che vengano distribuiti nella cartella App_GlobalResources del server.

4. Se si utilizzano le risorse per localizzare il codice oltre al markup ASPX, lasciare il valore della proprietà **operazione di compilazione** di ogni file come **risorsa incorporata**. Se si usano i file di risorse solo per localizzare il markup, è possibile modificare facoltativamente il valore della proprietà dei file in **contenuto**. Per altre informazioni, vedere [localizzare le soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

5. Aprire ogni file di risorse e aggiungere stringhe localizzate, usando gli stessi ID di stringa in ogni file.

6. Nel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] markup per la pagina o il controllo aspx sostituire le stringhe hardcoded con i valori che usano il formato seguente:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Ad esempio, per localizzare il testo di un controllo etichetta in una pagina dell'applicazione, modificare:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     to

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. Premere il tasto **F5** per compilare ed eseguire l'applicazione.

8. In SharePoint modificare la lingua di visualizzazione dal valore predefinito.

     Le stringhe localizzate vengono visualizzate nell'applicazione. Per visualizzare le risorse localizzate, è necessario che nel server SharePoint sia installato un Language Pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedere anche
- [Localizzare le soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)
- [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
- [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md)
