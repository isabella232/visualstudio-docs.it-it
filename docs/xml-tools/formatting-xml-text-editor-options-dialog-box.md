---
title: Formattazione, XML, Editor di testo, finestra di dialogo Opzioni
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05ddfcb0613dac08fb6e4323062f87475bd8f0d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938592"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Opzioni di formattazione, XML, editor di testo, finestra di dialogo

Questa finestra di dialogo consente di specificare le impostazioni di formattazione dell'editor XML. È possibile accedere la **le opzioni** dalla finestra di dialogo il **strumenti** menu.

> [!NOTE]
> Queste impostazioni sono disponibili quando si seleziona il **Editor di testo** cartella, la **XML** cartella e quindi il **formattazione** opzione il **opzioni** finestra di dialogo.

## <a name="attributes"></a>Attributi
 **Mantieni la formattazione manuale degli attributi**

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

## <a name="mixed-content"></a>contenuto misto
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

- [Proprietà di documento XML, finestra proprietà](../xml-tools/xml-document-properties-properties-window.md)
- [Componenti dell'Editor XML](../xml-tools/xml-editor-components.md)