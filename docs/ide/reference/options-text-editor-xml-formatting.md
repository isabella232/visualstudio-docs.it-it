---
title: Opzioni, Editor di testo, XML, Formattazione
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0d8420df205d49df3c6799e62adbc4e759a4aed2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826520"
---
# <a name="options-text-editor-xml-formatting"></a>Opzioni, Editor di testo, XML, Formattazione

Usare la pagina delle proprietà **Formattazione** per specificare la formattazione di elementi e attributi nei documenti XML. Per aprire la finestra di dialogo **Opzioni**, fare clic sul menu **Strumenti** e quindi su **Opzioni**. Per accedere alla finestra delle proprietà **Formattazione**, espandere **Editor di testo** > **XML** > nodo **Formattazione**.

## <a name="attributes"></a>Attributi

**Mantieni la formattazione manuale degli attributi**

Consente di non riformattare gli attributi. Questa è l'impostazione predefinita.

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

- [Procedura: Creare documentazione XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Generazione di codice](../code-generation-in-visual-studio.md)