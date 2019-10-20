---
title: Formattazione, XML, editor di testo, finestra di dialogo Opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670965"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formattazione, XML, Editor di testo, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa finestra di dialogo consente di specificare le impostazioni di formattazione dell'editor XML. È possibile accedere alla finestra di dialogo **Opzioni** dal menu **strumenti** .

> [!NOTE]
> Queste impostazioni sono disponibili quando si seleziona la cartella **editor di testo** , la cartella **XML** e quindi l'opzione **formattazione** nella finestra di dialogo **Opzioni** .

## <a name="attributes"></a>Attributi
 **Mantieni la formattazione manuale degli attributi** Gli attributi non vengono riformattati. Questa è l'impostazione predefinita.

> [!NOTE]
> Se gli attributi si trovano su più righe, l'editor fa rientrare ogni riga degli attributi in base al rientro dell'elemento padre.

 **Allinea ogni attributo su una riga a se stante** Allinea il secondo e gli attributi successivi verticalmente in modo da corrispondere al rientro del primo attributo. Il testo XML seguente è un esempio di come vengono allineati gli attributi.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Riformatta automaticamente
 Quando si **Incolla dagli Appunti** Riformatta il testo XML incollato dagli Appunti.

 **Al completamento del tag di fine** Riformatta l'elemento quando il tag di fine viene completato.

## <a name="mixed-content"></a>Contenuto misto
 **Mantieni contenuto misto per impostazione predefinita** Determina se l'editor riformatta il contenuto misto. Per impostazione predefinita l'editor tenta di riformattare il contenuto misto, a meno che il contenuto non venga rilevato in un ambito `xml:space="preserve"`.

 Se un elemento contiene una combinazione di testo e markup, il contenuto viene considerato misto. Di seguito viene riportato un esempio di elemento con contenuto misto.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Vedere anche
 [Proprietà del documento XML,](../xml-tools/xml-document-properties-properties-window.md) [componenti dell'editor XML](../xml-tools/xml-editor-components.md) della finestra Proprietà
