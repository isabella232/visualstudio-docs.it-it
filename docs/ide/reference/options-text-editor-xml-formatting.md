---
title: Opzioni, Editor di testo, XML, Formattazione
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e20b2f7ebe351aa050ea66468fb33aba8e4a31bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969267"
---
# <a name="options-text-editor-xml-formatting"></a>Opzioni, Editor di testo, XML, Formattazione

Usare la pagina delle opzioni **Formattazione** per specificare la formattazione di elementi e attributi nei documenti XML. Per accedere alle opzioni di formattazione XML, scegliere **Strumenti** > **Opzioni** > **Editor di testo** > **XML**, quindi scegliere **Formattazione**.

## <a name="attributes"></a>Attributi

**Mantieni la formattazione manuale degli attributi**

Consente di non riformattare gli attributi. Questa è l'impostazione predefinita.

> [!NOTE]
> Se gli attributi si trovano su più righe, l'editor fa rientrare ogni riga degli attributi in base al rientro dell'elemento padre.

**Allinea ogni attributo su una riga separata**

Allinea verticalmente il secondo attributo e i successivi in base al rientro del primo attributo. Il testo XML seguente è un esempio di allineamento degli attributi:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Riformatta automaticamente

**All'inserimento degli Appunti**

Riformatta il testo XML incollato dagli Appunti.

**Al completamento del tag di fine**

Riformatta l'elemento quando il tag di fine è completato.

## <a name="mixed-content"></a>Contenuto misto

**Formatta contenuto misto per impostazione predefinita.**

Tenta di riformattare il contenuto misto, a meno che il contenuto non venga rilevato in un ambito `xml:space="preserve"`. Questa è l'impostazione predefinita.

Se un elemento contiene una combinazione di testo e markup, il contenuto viene considerato misto. Di seguito viene riportato un esempio di elemento con contenuto misto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Vedere anche

- [Opzioni, XML, Varie](options-text-editor-xml-miscellaneous.md)
- [Strumenti XML in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)