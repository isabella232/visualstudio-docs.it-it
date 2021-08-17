---
title: Eseguire una trasformazione XSLT
description: Informazioni su come usare l'editor XML per associare un foglio di stile XSLT a un documento XML, eseguire una trasformazione XSLT e visualizzare l'output.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: c578007a79991c165ab6a88848c5428fe4e6e5e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025121"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procedura: Eseguire una trasformazione XSLT dall'editor XML

L'editor XML consente di associare un foglio di stile XSLT a un documento XML, eseguire la trasformazione e visualizzare l'output. L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.

La **proprietà Output** specifica il nome file per l'output. Se la **proprietà Output** è vuota, viene generato un nome file nella directory temporanea. L'estensione del file è basata `xsl:output` sull'elemento nel foglio di stile e può essere .*xml*, . *txt* o . *htm*.

Se la **proprietà Output** specifica un nome file con un oggetto . *htm* o . *estensione HTML,* l'output XSLT viene visualizzato in anteprima usando un Web browser. Tutte le altre estensioni di file vengono aperte usando l'editor predefinito scelto Visual Studio. Ad esempio, se l'estensione del file è . *xml*, Visual Studio l'editor XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Eseguire una trasformazione XSLT da un file XML

1. Aprire un documento XML nell'editor XML.

2. Associare un foglio di stile XSLT al documento XML.

    - Aggiungere un'istruzione di elaborazione `xml-stylesheet` al documento XML. Ad esempio, aggiungere la riga seguente al prologo del documento: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -oppure-

    - Aggiungere il foglio di stile XSLT usando la **finestra** Proprietà. Con il file XML aperto nell'editor, fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor e scegliere **Proprietà**. Nella finestra **Proprietà** fare clic nel campo **Foglio di** stile e scegliere il pulsante Sfoglia (...). Selezionare il foglio di stile XSLT e quindi scegliere **Apri.**

3. Sulla barra dei menu scegliere **XML**  >  **Avvia XSLT senza eseguire debug.** In caso contrario, **premere** + **CTRL ALT** + **F5.**

   L'output della trasformazione XSLT viene visualizzato in una nuova finestra del documento.

   > [!NOTE]
   > Se al documento XML non è associato alcun foglio di stile, viene visualizzata una finestra di dialogo con la richiesta di specificare il foglio di stile da usare.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Eseguire una trasformazione XSLT da un foglio di stile XSLT

1. Aprire un foglio di stile XSLT nell'editor XML.

2. Specificare un documento XML nel **campo Input** della finestra **Proprietà del** documento.

   > [!NOTE]
   > Il documento XML è il documento di input usato per la trasformazione. Se all'avvio della trasformazione XSLT non viene specificato un documento, viene visualizzata la finestra di dialogo **Apri** file in cui è possibile specificare un documento.

3. Sulla barra dei menu scegliere **XML**  >  **Avvia XSLT senza eseguire debug.** In caso contrario, **premere** + **CTRL ALT** + **F5.**

   L'output della trasformazione XSLT viene visualizzato in una nuova finestra del documento.

## <a name="specify-an-output-file-name"></a>Specificare un nome di file di output

È possibile specificare un nome di file di output per i file XML e XSL. Aprire la **finestra** Proprietà e specificare un nome file nel **campo Output.**

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
