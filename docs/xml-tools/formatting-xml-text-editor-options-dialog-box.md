---
title: Formattazione, XML, Editor di testo, finestra di dialogo Opzioni
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f92ced5ca5ac007969a06cec7f253617ee293e3
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548791"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formattazione, XML, editor di testo, finestra di dialogo Opzioni

Questa finestra di dialogo consente di specificare le impostazioni di formattazione dell'editor XML. È possibile accedere il **opzioni** dalla finestra di dialogo di **strumenti** menu.

> [!NOTE]
> Queste impostazioni sono disponibili quando si seleziona il **Editor di testo** cartella, il **XML** cartella, quindi il **formattazione** opzione il **opzioni** la finestra di dialogo.

## <a name="attributes"></a>Attributi
 **Mantenere la formattazione manuale degli attributi**

 Gli attributi non vengono riformattati. Questa è l'impostazione predefinita.

> [!NOTE]
> Se gli attributi si trovano su più righe, l'editor fa rientrare ogni riga degli attributi in base al rientro dell'elemento padre.

 **Allinea ogni attributo su una riga separata**

 Allinea verticalmente il secondo attributo e i successivi in base al rientro del primo attributo. Il testo XML seguente è un esempio di come vengono allineati gli attributi.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Riformatta automaticamente
 **Quando si incolla dagli Appunti**

 Riformatta il testo XML incollato dagli Appunti.

 **Al completamento del tag di fine**

 Riformatta l'elemento quando il tag di fine è completato.

## <a name="mixed-content"></a>Contenuto misto
 **Mantieni contenuto misto per impostazione predefinita**

 Determina se l'editor riformatta o meno il contenuto misto. Per impostazione predefinita l'editor tenta di riformattare il contenuto misto, a meno che il contenuto non venga rilevato in un ambito `xml:space="preserve"`.

 Se un elemento contiene una combinazione di testo e markup, il contenuto viene considerato misto. Di seguito viene riportato un esempio di elemento con contenuto misto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Vedere anche

- [Proprietà del documento XML, finestra proprietà](../xml-tools/xml-document-properties-properties-window.md)
- [Componenti dell'Editor XML](../xml-tools/xml-editor-components.md)