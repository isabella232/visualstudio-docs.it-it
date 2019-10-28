---
title: 'Procedura: aggiungere comandi a menu di scelta rapida'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 82c26022f0c88f1ce125c64f5ec3b2df8d20346e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986021"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Procedura: aggiungere comandi a menu di scelta rapida
  Questo argomento illustra come aggiungere comandi a un menu di scelta rapida in un'applicazione di Office usando un componente aggiuntivo VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Per aggiungere comandi al menu di scelta rapida in Office

1. Aggiungere un elemento **Barra multifunzione (XML)** in un progetto di componente aggiuntivo VSTO o a livello di documento. Per altre informazioni, vedere [procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md). In

2. **Esplora soluzioni**selezionare **ThisAddin.cs** o **ThisAddin.vb**.

3. Sulla barra dei menu scegliere **Visualizza** > **Codice**.

     Il file di classe **ThisAddin** viene aperto nell'editor di codice.

4. Aggiungere il codice seguente alla classe **ThisAddIn** . Questo codice esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce la classe XML della barra multifunzione all'applicazione Office.

     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]

5. In **Esplora soluzioni**selezionare il file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione è denominato *Ribbon1. XML*.

6. Sulla barra dei menu scegliere **Visualizza** > **Codice**.

     Il file XML della barra multifunzione viene aperto nell'editor di codice.

7. Nell'editor di codice aggiungere codice XML che descriva il menu di scelta rapida e il controllo da aggiungere al menu di scelta rapida.

     Nell'esempio seguente viene aggiunto un pulsante, un controllo e un controllo della raccolta al menu di scelta rapida per un documento di Word. L'ID del controllo di questo menu di scelta rapida è ContextMenuText. Per un elenco completo degli ID di controllo dei collegamenti di Office 2010, vedere file della Guida di Office [2010: identificatori di controllo dell'interfaccia utente di Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

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

8. In **Esplora soluzioni**scegliere **MyRibbon.cs** o **MyRibbon.vb**.

9. Aggiungere un metodo di callback alla classe `Ribbon1` per ogni controllo che si desidera gestire.

     Il metodo di callback seguente consente di gestire il pulsante **My Button** . Questo codice aggiunge una stringa al documento attivo in corrispondenza della posizione corrente del cursore.

     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]

## <a name="see-also"></a>Vedere anche
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Procedura dettagliata: creare menu di scelta rapida per i segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Personalizzare i menu di scelta rapida in Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
