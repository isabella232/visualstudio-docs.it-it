---
title: Eseguire una trasformazione XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84b1c6303da4c0db39da1b3585a7d4548560feb
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526373"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procedura: Eseguire una trasformazione XSLT dall'editor XML

L'editor XML consente di associare un foglio di stile XSLT a un documento XML, eseguire la trasformazione e visualizzare l'output. L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.

Il **Output** proprietà specifica il nome del file per l'output. Se il **Output** proprietà è vuota, viene generato un nome di file nella directory temporanea. L'estensione del file si basa sul `xsl:output` elemento nello stile foglio e può essere. *XML*,. *txt* o. *htm*.

Se il **Output** proprietà consente di specificare un nome file con un. *htm* o. *HTML* estensione, l'output XSLT è in anteprima con un web browser. Tutte le altre estensioni di file aperti con l'editor predefinito scelto da Visual Studio. Ad esempio, se è l'estensione di file. *xml*, Visual Studio Usa l'editor XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Eseguire una trasformazione XSLT da un file XML

1. Aprire un documento XML nell'editor XML.

2. Associare un foglio di stile XSLT al documento XML.

    - Aggiungere un'istruzione di elaborazione `xml-stylesheet` al documento XML. Ad esempio, aggiungere la riga seguente al prologo del documento: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -oppure-

    - Aggiungere il foglio di stile XSLT usando la **proprietà** finestra. Con il file XML aperto nell'editor, fare clic in un punto qualsiasi nell'editor e scegliere **proprietà**. Nel **delle proprietà** finestra, fare clic nel **foglio di stile** campo e scegliere il pulsante Sfoglia (...). Selezionare il foglio di stile XSLT e quindi scegliere **aperto**.

3. Nella barra dei menu, scegliere **XML** > **avvia XSLT senza debug**. In alternativa, premere **Ctrl**+**Alt**+**F5**.

   L'output dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.

   > [!NOTE]
   > Se al documento XML non è associato alcun foglio di stile, viene visualizzata una finestra di dialogo con la richiesta di specificare il foglio di stile da usare.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Eseguire una trasformazione XSLT da un foglio di stile XSLT

1. Aprire un foglio di stile XSLT nell'editor XML.

2. Specificare un documento XML nel **Input** campo del documento **proprietà** finestra.

   > [!NOTE]
   > Il documento XML è il documento di input usato per la trasformazione. Se un documento non viene specificato quando la trasformazione XSLT viene avviata, il **Apri File** verrà visualizzata la finestra di dialogo ed è possibile specificare un documento in quel momento.

3. Nella barra dei menu, scegliere **XML** > **avvia XSLT senza debug**. In alternativa, premere **Ctrl**+**Alt**+**F5**.

   L'output dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.

## <a name="specify-an-output-file-name"></a>Specificare un nome di file di output

È possibile specificare un nome di file di output per i file XML e XSL. Aprire il **delle proprietà** finestra e specificare un nome di file nel **Output** campo.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)