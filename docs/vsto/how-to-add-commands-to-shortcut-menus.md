---
title: 'Procedura: aggiungere comandi al menu di scelta rapida | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
ms.assetid: 9a848817-db11-4294-8f6f-9181ab87aadd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa5578a25b6bb877f241b9a5c8b7ccd876e7b773
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Procedura: Aggiungere comandi a menu di scelta rapida
  Questo argomento illustra come aggiungere comandi a un menu di scelta rapida in un'applicazione di Office con un componente aggiuntivo VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Per aggiungere comandi al menu di scelta rapida in Office  
  
1.  Aggiungere un elemento **Barra multifunzione (XML)** in un progetto di componente aggiuntivo VSTO o a livello di documento. Per altre informazioni, vedere [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md). In  
  
2.  **Esplora soluzioni**selezionare **ThisAddin.cs** o **ThisAddin.vb**.  
  
3.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
     Il file di classe **ThisAddin** viene aperto nell'editor di codice.  
  
4.  Aggiungere il codice seguente alla classe **ThisAddIn** . Questo codice esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe Ribbon XML all'applicazione di Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  In **Esplora soluzioni**selezionare il file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione è denominato Ribbon1.xml.  
  
6.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
     Il file XML della barra multifunzione viene aperto nell'editor di codice.  
  
7.  Nell'editor di codice aggiungere codice XML che descriva il menu di scelta rapida e il controllo da aggiungere al menu di scelta rapida.  
  
     Nell'esempio seguente viene aggiunto un pulsante, un controllo e un controllo della raccolta al menu di scelta rapida per un documento di Word. L'ID del controllo di questo menu di scelta rapida è ContextMenuText. Per un elenco completo di controllo di scelta rapida di Office 2010 ID, vedere [file della Guida di Office 2010: identificatori utente Office Fluent interfaccia controllo](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```  
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
  
8.  In **Esplora soluzioni**scegliere **MyRibbon.cs** o **MyRibbon.vb**.  
  
9. Aggiungere un metodo di callback alla classe `Ribbon1` per ogni controllo da gestire.  
  
     Il metodo di callback seguente consente di gestire il pulsante **My Button** . Questo codice aggiunge una stringa al documento attivo in corrispondenza della posizione corrente del cursore.  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Procedura dettagliata: Creazione di menu di scelta rapida per segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Personalizzazione di menu di scelta rapida in Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  