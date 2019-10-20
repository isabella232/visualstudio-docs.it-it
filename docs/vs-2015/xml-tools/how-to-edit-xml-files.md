---
title: 'Procedura: modificare file XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c099839cda87819ec0ec7932c2b2e6aa7698fa52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670875"
---
# <a name="how-to-edit-xml-files"></a>Procedura: modificare i file XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor XML è il nuovo editor per file XML. Può essere usato per un file XML autonomo o per un file associato a un progetto Visual Studio. L'editor XML è associato alle estensioni di file seguenti: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt e .vssettings. L'editor XML è inoltre associato a qualsiasi altro tipo di file per il quale non è stato registrato un editor specifico e che presenta un contenuto XML o DTD.

> [!NOTE]
> I documenti XHTML sono gestiti dall'editor HTML.

### <a name="to-edit-an-xml-file"></a>Per modificare un file XML

1. Fare doppio clic sul file che si desidera modificare.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Per aggiungere un nuovo file XML a un progetto

1. Scegliere **Aggiungi nuovo elemento**dal menu **progetto** .

2. Selezionare **file XML** dal riquadro **modelli** .

3. Immettere il nome del file nel campo **nome** e fare clic su **Aggiungi**.

     Il file XML viene aggiunto al progetto e aperto nell'editor XML. Il file contiene la dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8" ?>`.

### <a name="to-add-an-existing-xml-file-to-a-project"></a>Per aggiungere un file XML esistente a un progetto

1. Scegliere **Aggiungi elemento esistente**dal menu **progetto** .

     Verrà visualizzata la finestra di dialogo **Aggiungi elemento esistente** .

2. Selezionare un file XML e premere **Aggiungi**.

### <a name="to-create-a-new-xml-or-xslt-file"></a>Per creare un nuovo file XML o XSLT

1. Scegliere **nuovo**dal menu **file** .

     Verrà visualizzata la finestra di dialogo **nuovo file** .

2. Selezionare il **file XML** per creare un nuovo file XML. in alternativa, selezionare **file XSLT** per creare un nuovo foglio di stile XSLT.

3. Fare clic su **Apri**.

### <a name="to-create-a-project-for-xml-files"></a>Per creare un progetto per i file XML

1. Scegliere **nuovo**dal menu **file** , quindi selezionare **progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.

2. Selezionare il linguaggio del codice desiderato, selezionare **progetto vuoto**, quindi fare clic su **OK**.

3. Aggiunta di file XML al progetto.

     L'editor XML individua gli schemi aggiunti al progetto e li usa per la convalida e IntelliSense in qualsiasi file XML, schema o file XSLT che vengono modificati mentre il progetto è aperto.

## <a name="see-also"></a>Vedere anche
 Proprietà del documento XML dell' [editor XML](../xml-tools/xml-editor.md) [, finestra Proprietà](../xml-tools/xml-document-properties-properties-window.md) [procedura: creare uno schema XML da un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
