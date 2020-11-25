---
title: Eseguire una trasformazione XSLT
description: Viene illustrato come utilizzare l'editor XML per associare un foglio di stile XSLT a un documento XML, eseguire una trasformazione XSLT e visualizzare l'output.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1c7165f301c82dfaf5aa066a3e15bd7ab244089
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970244"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procedura: eseguire una trasformazione XSLT dall'editor XML

L'editor XML consente di associare un foglio di stile XSLT a un documento XML, eseguire la trasformazione e visualizzare l'output. L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.

La proprietà **output** specifica il nome file per l'output. Se la proprietà **output** è vuota, nella directory temporanea viene generato un nome file. L'estensione del file è basata sull' `xsl:output` elemento del foglio di stile e può essere.*XML*,. *txt* o. *htm*.

Se la proprietà di **output** specifica un nome di file con un oggetto. *htm* o. estensione *HTML* , l'output XSLT viene visualizzato in anteprima usando un Web browser. Tutte le altre estensioni di file vengono aperte usando l'editor predefinito scelto da Visual Studio. Ad esempio, se l'estensione del file è. *XML*, Visual Studio usa l'editor XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Eseguire una trasformazione XSLT da un file XML

1. Aprire un documento XML nell'editor XML.

2. Associare un foglio di stile XSLT al documento XML.

    - Aggiungere un'istruzione di elaborazione `xml-stylesheet` al documento XML. Ad esempio, aggiungere la riga seguente al prologo del documento: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -oppure-

    - Aggiungere il foglio di stile XSLT utilizzando la finestra **Proprietà** . Con il file XML aperto nell'editor, fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor e scegliere **Proprietà**. Nella finestra **Proprietà** fare clic nel campo **foglio di stile** e scegliere il pulsante Sfoglia (...). Selezionare il foglio di stile XSLT, quindi scegliere **Apri**.

3. Sulla barra dei menu scegliere **XML**  >  **Avvia XSLT senza debug**. In alternativa, premere **CTRL** + **ALT** + **F5**.

   L'output della trasformazione XSLT viene visualizzato in una nuova finestra del documento.

   > [!NOTE]
   > Se al documento XML non è associato alcun foglio di stile, viene visualizzata una finestra di dialogo con la richiesta di specificare il foglio di stile da usare.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Eseguire una trasformazione XSLT da un foglio di stile XSLT

1. Aprire un foglio di stile XSLT nell'editor XML.

2. Specificare un documento XML nel campo di **input** della finestra **Proprietà** del documento.

   > [!NOTE]
   > Il documento XML è il documento di input usato per la trasformazione. Se un documento non viene specificato al momento dell'avvio della trasformazione XSLT, viene visualizzata la finestra di dialogo **Apri file** in cui è possibile specificare un documento.

3. Sulla barra dei menu scegliere **XML**  >  **Avvia XSLT senza debug**. In alternativa, premere **CTRL** + **ALT** + **F5**.

   L'output della trasformazione XSLT viene visualizzato in una nuova finestra del documento.

## <a name="specify-an-output-file-name"></a>Specificare un nome di file di output

È possibile specificare un nome di file di output per i file XML e XSL. Aprire la finestra **Proprietà** e specificare un nome di file nel campo **output** .

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
