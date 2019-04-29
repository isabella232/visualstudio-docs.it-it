---
title: 'Procedura: di file XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b25eebad9efc70e4fda45131e232983e81961625
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840369"
---
# <a name="how-to-edit-xml-files"></a>Procedura: Modificare i file XML

L'editor XML è il nuovo editor per i file XML. Può essere usato per un file XML autonomo o per un file associato a un progetto Visual Studio. L'editor XML è associato con le estensioni di file seguenti: *config*, *DTD*, *XML*, *XSD*, *. XDR*, *XSL*, *XSLT*, e *vssettings*. L'editor XML è anche associato a qualsiasi altro tipo di file che non dispone di alcuna specifica dell'editor registrata e che contiene il contenuto XML o DTD.

> [!NOTE]
> I documenti XHTML sono gestiti dall'editor HTML.

Per modificare un file XML, fare doppio clic sul file di cui che si desidera modificare.

## <a name="add-a-new-xml-file-to-a-project"></a>Aggiungere un nuovo file XML a un progetto

1. Dal **Project** dal menu **Aggiungi nuovo elemento**.

2. Selezionare **File XML** dalle **modelli** riquadro.

3. Immettere il nome del file nei **Name** campo e premere **Add**.

   Il file XML viene aggiunto al progetto e verrà aperto nell'editor XML. Il file contiene la dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Aggiungere un file XML esistente a un progetto

1. Dal **Project** dal menu **Aggiungi elemento esistente**.

   Il **Aggiungi elemento esistente** verrà visualizzata la finestra di dialogo.

2. Selezionare un file XML e premere **Add**.

## <a name="create-a-new-xml-or-xslt-file"></a>Creare un nuovo file XML o XSLT

1. Dal **File** dal menu **New**.

   Il **nuovo File** verrà visualizzata la finestra di dialogo.

2. Selezionare **File XML** per creare un nuovo file XML; o, selezionare **File XSLT** per creare un nuovo foglio di stile XSLT.

3. Fare clic su **Apri**.

## <a name="create-an-empty-project-for-xml-files"></a>Creare un progetto vuoto per i file XML

::: moniker range="vs-2017"

1. Dal **File** dal menu **New** > **progetto**.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Selezionare il linguaggio del codice di propria scelta, seleziona **progetto vuoto**.

3. Fare clic su **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dal **File** dal menu **New** > **progetto**.

2. Immettere **progetto vuoto** nella casella di ricerca di modello, selezionare la **progetto vuoto (.NET Framework)** modello e quindi fare clic su **Next**.

3. Scegliere **Crea**.

::: moniker-end

4. Aggiunta di file XML al progetto.

   L'editor XML individua gli schemi che aggiunti al progetto e li utilizza per la convalida e IntelliSense in XML, schemi o i file XSLT che vengono modificati mentre il progetto è aperto.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)
- [Proprietà di documento XML, finestra proprietà](../xml-tools/xml-document-properties-properties-window.md)
- [Procedura: Creare uno schema XML da un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)