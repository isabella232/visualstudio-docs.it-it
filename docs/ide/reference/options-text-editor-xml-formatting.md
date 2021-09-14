---
title: Opzioni, Editor di testo, XML, Formattazione
description: Informazioni su come usare la pagina Formattazione nella sezione XML per specificare la formattazione di elementi e attributi nei documenti XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 4d870026d55cb092b005b0148f392cf29181380e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628632"
---
# <a name="options-text-editor-xml-formatting"></a>Opzioni, Editor di testo, XML, Formattazione

Usare la pagina delle opzioni **Formattazione** per specificare la formattazione di elementi e attributi nei documenti XML. Per accedere alle opzioni di formattazione XML, **scegliere** Strumenti  >  **Opzioni** Editor  >  **di testo**  >  **XML** e quindi Scegliere **Formattazione**.

## <a name="attributes"></a>Attributi

**Mantieni la formattazione manuale degli attributi**

Consente di non riformattare gli attributi. È l'impostazione predefinita.

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

**Incollare dagli Appunti**

Consente di riformattare il testo XML incollato dagli Appunti.

**Al completamento del tag di fine**

Consente di riformattare l'elemento al completamento del tag di fine.

## <a name="mixed-content"></a>Contenuto misto

**Formatta contenuto misto per impostazione predefinita**

Viene riformattato il contenuto misto, tranne quando il contenuto si trova in un ambito `xml:space="preserve"`. È l'impostazione predefinita.

Se un elemento contiene testo e markup, il contenuto viene considerato misto. Di seguito viene riportato un esempio di elemento con contenuto misto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Vedi anche

- [Opzioni, XML, Varie](options-text-editor-xml-miscellaneous.md)
- [Strumenti XML in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
