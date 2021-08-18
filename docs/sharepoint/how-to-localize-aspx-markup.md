---
title: 'Procedura: Localizzare il markup ASPX | Microsoft Docs'
description: Informazioni su come localizzare il markup ASPX in SharePoint sostituendo i valori stringa hard-coded con espressioni che fanno riferimento a risorse localizzate.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d80157fc2468c5d6fe78ae88cfa0f940917888a8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084272"
---
# <a name="how-to-localize-aspx-markup"></a>Procedura: Localizzare il markup ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Le pagine (aspx) usano in genere valori stringa hard-coded. Per localizzare queste stringhe, sostituirle con espressioni che fanno riferimento a risorse localizzate.

## <a name="localize-aspx-markup"></a>Localizzare il markup ASPX

#### <a name="to-localize-aspx-markup"></a>Per localizzare il markup ASPX

1. Aggiungere file di risorse separati: uno per la lingua predefinita e uno per ogni lingua localizzata.

     Se si sta localizzando solo markup e non codice, aggiungere un elemento di progetto File di risorse globali. Se si localizza codice e markup, aggiungere un elemento di progetto File di risorse.

    1. Per aggiungere un file di risorse globali, in **Esplora soluzioni** aprire il menu di scelta rapida per un elemento SharePoint progetto e quindi scegliere **Aggiungi**  >  **nuovo elemento.** Nel nodo SharePoint **2010** scegliere il **modello File di risorse** globali.

    2. Per aggiungere un file di risorse, in **Esplora soluzioni** aprire il menu di scelta rapida per un elemento SharePoint progetto e quindi scegliere **Aggiungi**  >  **nuovo elemento**. Nel nodo **Visual Basic** o **Visual C#** scegliere il **modello File di** risorse.

    > [!NOTE]
    > Assicurarsi di aggiungere i file di risorse a un elemento SharePoint progetto per abilitare la proprietà Tipo di distribuzione. Questa proprietà è necessaria più avanti in questa procedura. Se la soluzione non ha un elemento SharePoint progetto, è possibile aggiungere un SharePoint Project vuoto e rimuovere il relativo file *Elements.xml* predefinito.

2. Assegnare al file di risorse della lingua predefinito un nome a scelta, accodato all'estensione *resx,* ad esempio MyAppResources.resx. Utilizzare lo stesso nome base per ogni file di risorse localizzato, ma aggiungere l'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] delle impostazioni cultura. Ad esempio, assegnare a una risorsa localizzata in *tedesco MyAppResources.de-DE.resx*.

3. Modificare il valore della **proprietà Tipo** di distribuzione di ogni file di risorse in **AppGlobalResource** per distribuirlo nella cartella App_GlobalResources server.

4. Se si usano le risorse per localizzare il codice oltre  al markup ASPX, lasciare il valore della proprietà Azione di compilazione di ogni file come **Risorsa incorporata**. Se si usano i file di risorse solo per localizzare il markup, è possibile modificare facoltativamente il valore della proprietà dei file in **Contenuto**. Per altre informazioni, vedere [Localizzare SharePoint soluzioni](../sharepoint/localizing-sharepoint-solutions.md).

5. Aprire ogni file di risorse e aggiungere stringhe localizzate, usando gli stessi ID stringa in ogni file.

6. Nel markup per la pagina o il controllo ASPX sostituire le stringhe [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] hard-coded con valori che usano il formato seguente:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Ad esempio, per localizzare il testo per un controllo etichetta in una pagina dell'applicazione, è necessario modificare:

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

7. Premere **F5 per** compilare ed eseguire l'applicazione.

8. In SharePoint modificare la lingua di visualizzazione rispetto all'impostazione predefinita.

     Le stringhe localizzate vengono visualizzate nell'applicazione. Per visualizzare le risorse localizzate, nel server SharePoint deve essere installato un language pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedi anche
- [Localizzare SharePoint soluzioni](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: Localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)
- [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
- [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)
