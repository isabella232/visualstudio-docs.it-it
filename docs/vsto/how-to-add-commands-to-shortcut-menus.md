---
title: 'Procedura: Aggiungere comandi ai menu di scelta rapida'
description: Informazioni su come aggiungere comandi a un menu di scelta rapida in un'applicazione Office usando un VSTO componente aggiuntivo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a85b45dbe8ffd616b89078795f0cd9ffe11da7fd97e92339dab8ed2162ae2d2f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424209"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Procedura: Aggiungere comandi ai menu di scelta rapida
  In questo argomento viene illustrato come aggiungere comandi a un menu di scelta rapida in un'applicazione Office utilizzando un VSTO componente aggiuntivo.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Per aggiungere comandi al menu di scelta rapida in Office

1. Aggiungere un elemento **Barra multifunzione (XML)** in un progetto di componente aggiuntivo VSTO o a livello di documento. Per altre informazioni, vedere [Procedura: Iniziare a personalizzare la barra multifunzione.](../vsto/how-to-get-started-customizing-the-ribbon.md) In

2. **Esplora soluzioni** selezionare **ThisAddin.cs** o **ThisAddin.vb**.

3. Sulla barra dei menu scegliere **Visualizza**  >  **codice.**

     Il file di classe **ThisAddin** viene aperto nell'editor di codice.

4. Aggiungere il codice seguente alla classe **ThisAddIn** . Questo codice esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce la classe XML della barra multifunzione all'applicazione Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet1":::

5. In **Esplora soluzioni** selezionare il file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione è *denominatoRibbon1.xml*.

6. Sulla barra dei menu scegliere **Visualizza**  >  **codice.**

     Il file XML della barra multifunzione viene aperto nell'editor di codice.

7. Nell'editor di codice aggiungere codice XML che descriva il menu di scelta rapida e il controllo da aggiungere al menu di scelta rapida.

     Nell'esempio seguente viene aggiunto un pulsante, un controllo e un controllo della raccolta al menu di scelta rapida per un documento di Word. L'ID del controllo di questo menu di scelta rapida è ContextMenuText. Per un elenco completo degli ID di controllo Office 2010, vedere i file della Guida di [Office 2010:](https://www.microsoft.com/download/details.aspx?id=6627)Office di controllo dell'interfaccia utente Fluent.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />
          <menu id="MySubMenu" label="My Submenu" >
            <button id="MyButton2" label="Button on submenu" />
          </menu>
          <gallery id="galleryOne" label="My Gallery">
            <item id="item1" imageMso="HappyFace" />
            <item id="item2" imageMso="HappyFace" />
            <item id="item3" imageMso="HappyFace" />
            <item id="item4" imageMso="HappyFace" />
          </gallery>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

8. In **Esplora soluzioni** scegliere **MyRibbon.cs** o **MyRibbon.vb**.

9. Aggiungere un metodo di callback `Ribbon1` alla classe per ogni controllo che si vuole gestire.

     Il metodo di callback seguente consente di gestire il pulsante **My Button** . Questo codice aggiunge una stringa al documento attivo in corrispondenza della posizione corrente del cursore.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs" id="Snippet2":::

## <a name="see-also"></a>Vedi anche
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Procedura dettagliata: Creare menu di scelta rapida per i segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
- [Personalizzare i menu di scelta rapida in Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
