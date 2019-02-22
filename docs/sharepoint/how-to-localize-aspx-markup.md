---
title: 'Procedura: Localizzare il Markup ASPX | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 433111855aab18bea412e5774cfe7a2fca2b2a7b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609826"
---
# <a name="how-to-localize-aspx-markup"></a>Procedura: Localizzare il markup ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine (con estensione aspx) usano in genere i valori di stringa hardcoded. Per queste stringhe da localizzare, sostituirli con espressioni che fanno riferimento alle risorse localizzate.

## <a name="localize-aspx-markup"></a>Localizzare il markup ASPX

#### <a name="to-localize-aspx-markup"></a>Per localizzare il markup ASPX

1.  Aggiungere file di risorse separati: uno per la lingua predefinita e uno per ogni lingua localizzata.

     Se si sta localizzando solo markup e non nel codice, aggiungere un elemento di progetto di File di risorse globali. Se si sta localizzando codice e markup, aggiungere un elemento di progetto di File di risorse.

    1.  Per aggiungere un File di risorse globali, in **Esplora soluzioni**, aprire il menu di scelta rapida per un elemento di progetto SharePoint e quindi scegliere **Add** > **nuovo elemento**. In SharePoint **2010** nodo, scegliere il **File di risorse globali** modello.

    2.  Per aggiungere un File di risorse, in **Esplora soluzioni**, aprire il menu di scelta rapida per un elemento di progetto SharePoint e quindi scegliere **Add** > **nuovo elemento**. Sotto il **Visual Basic** oppure **Visual c#** nodo, scegliere il **File di risorse** modello.

    > [!NOTE]
    >  Assicurarsi di aggiungere i file di risorse a un elemento di progetto SharePoint per abilitare la proprietà del tipo di distribuzione. Questa proprietà è necessaria più avanti in questa procedura. Se la soluzione non ha un elemento del progetto SharePoint, è possibile aggiungere un progetto SharePoint vuoto e rimuovere sul valore predefinito *Elements* file.

2.  Assegnare un nome di propria scelta con i file di risorse di lingua predefinito un *resx* estensione, ad esempio MyAppResources. Utilizzare lo stesso nome base per ogni file di risorse localizzato, ma aggiungere l'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] delle impostazioni cultura. Ad esempio, nome un tedesco localizzata resource *MyAppResources.de-. resx*.

3.  Modificare il valore della **tipo di distribuzione** proprietà di ogni file di risorse da **AppGlobalResource** per fare in modo per distribuire nella cartella App_GlobalResources del server.

4.  Se si usa le risorse per localizzare codice oltre al markup ASPX, lasciare il valore di **Build Action** proprietà di ogni file impostato **risorsa incorporata**. Se si usa i file di risorse solo per localizzare il markup, è facoltativamente possibile modificare il valore della proprietà dei file da **contenuto**. Per altre informazioni, vedere [soluzioni SharePoint localizzare](../sharepoint/localizing-sharepoint-solutions.md).

5.  Aprire ogni file di risorse e aggiungere le stringhe localizzate, usando la stessa stringa di ID in ogni file.

6.  Nel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] markup della pagina ASPX o del controllo, sostituire le stringhe hardcoded con i valori che usano il formato seguente:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Ad esempio, per localizzare il testo per un controllo etichetta in una pagina applicazione, modificare:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     in

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7.  Scegliere il **F5** chiave per compilare ed eseguire l'applicazione.

8.  In SharePoint, cambiare la lingua di visualizzazione da quello predefinito.

     Le stringhe localizzate visualizzata nell'applicazione. Per visualizzare le risorse localizzate, il server di SharePoint deve avere installato un language pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedere anche
- [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: Localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)
- [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
- [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)
