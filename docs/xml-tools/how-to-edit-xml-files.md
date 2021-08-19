---
title: 'Procedura: modificare i file XML'
ms.date: 11/04/2016
description: Informazioni su come usare l'editor XML in Visual Studio modificare i file che contengono contenuto XML o DTD.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: d308fa0298297bf91313f611bc0efe791191f9ae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114485"
---
# <a name="how-to-edit-xml-files"></a>Procedura: Modificare file XML

L'editor XML è il nuovo editor per i file XML. Può essere usato per un file XML autonomo o per un file associato a un progetto Visual Studio. L'editor XML è associato alle estensioni di file *seguenti:.config*, *dtd*, *.xml*, *xsd*, *xdr*, *xsl*, *xslt* e *vssettings*. L'editor XML è inoltre associato a qualsiasi altro tipo di file che non dispone di un editor specifico registrato e che contiene contenuto XML o DTD.

> [!NOTE]
> I documenti XHTML sono gestiti dall'editor HTML.

Per modificare un file XML, aprire il file che si desidera modificare.

## <a name="add-a-new-xml-file-to-a-project"></a>Aggiungere un nuovo file XML a un progetto

1. Dal menu **Project** selezionare **Aggiungi nuovo elemento.**

2. Selezionare **File XML** nel **riquadro** Modelli.

3. Immettere il nome del file **nel campo Nome** e premere **Aggiungi.**

   Il file XML viene aggiunto al progetto e aperto nell'editor XML. Il file contiene la dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Aggiungere un file XML esistente a un progetto

1. Dal menu **Progetto** selezionare **Add Existing Item**(Aggiungi elemento esistente).

   Verrà **visualizzata la finestra di dialogo** Aggiungi elemento esistente .

2. Selezionare un file XML e premere **Aggiungi**.

## <a name="create-a-new-xml-or-xslt-file"></a>Creare un nuovo file XML o XSLT

1. Scegliere **Nuovo** dal menu **File.**

   Verrà visualizzata la finestra di dialogo **Nuovo file** .

2. Selezionare **File XML** per creare un nuovo file XML. oppure selezionare **File XSLT per** creare un nuovo foglio di stile XSLT.

3. Selezionare **Open** (Apri).

## <a name="create-an-empty-project-for-xml-files"></a>Creare un progetto vuoto per i file XML

::: moniker range="vs-2017"

1. Scegliere **Nuovo** dal  menu File > **Project**.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Selezionare il linguaggio di codice preferito e quindi selezionare il modello Project **vuoto (.NET Framework).**

3. Selezionare **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Scegliere **Nuovo** dal  menu File > **Project**.

2. Immettere **Vuoto Project** nella casella di ricerca del modello, selezionare il modello Project vuoto **(.NET Framework)** e quindi selezionare **Avanti.**

3. Selezionare **Crea**.

::: moniker-end

4. Aggiunta di file XML al progetto.

   L'editor XML trova gli schemi aggiunti a questo progetto e li usa per la convalida e IntelliSense in qualsiasi file XML, schema o XSLT modificato mentre il progetto è aperto.

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
- [Proprietà documento XML, finestra delle proprietà](../xml-tools/xml-document-properties-properties-window.md)
- [Procedura: Creare uno schema XML da un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
