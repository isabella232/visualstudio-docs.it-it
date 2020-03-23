---
title: Opzioni, Editor di testo, XML, Formattazione
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568139"
---
# <a name="options-text-editor-xml-formatting"></a>Opzioni, Editor di testo, XML, Formattazione

Usare la pagina delle opzioni **Formattazione** per specificare la formattazione di elementi e attributi nei documenti XML. Per accedere alle opzioni di formattazione XML, scegliere **Strumenti** > **Opzioni** > Editor > **testo****XML**, quindi **Formattazione**.

## <a name="attributes"></a>Attributes

**Mantieni la formattazione manuale degli attributi**

Consente di non riformattare gli attributi. Questa è l'impostazione predefinita.

> [!NOTE]
> Se gli attributi sono disposti su più righe, a ogni riga di attributi verrà applicato un rientro corrispondente al rientro dell'elemento padre.

**Allinea ogni attributo su una riga separata**

Il secondo attributo e i successivi vengono allineati verticalmente in modo da corrispondere al rientro del primo attributo. Il testo XML seguente è un esempio di allineamento degli attributi:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Riformatta automaticamente

**In cui incollare dagli Appunti**

Consente di riformattare il testo XML incollato dagli Appunti.

**Al completamento del tag di fine**

Consente di riformattare l'elemento al completamento del tag di fine.

## <a name="mixed-content"></a>Contenuto misto

**Formatta contenuto misto per impostazione predefinita**

Viene riformattato il contenuto misto, tranne quando il contenuto si trova in un ambito `xml:space="preserve"`. Questa è l'impostazione predefinita.

Se un elemento contiene testo e markup, il contenuto viene considerato misto. Di seguito viene riportato un esempio di elemento con contenuto misto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Vedere anche

- [Opzioni, XML, Varie](options-text-editor-xml-miscellaneous.md)
- [Strumenti XML in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
