---
title: "Procedura: eseguire una trasformazione XSLT dall'editor XML | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666541"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procedura: eseguire una trasformazione XSLT dall'editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor XML consente di associare un foglio di stile XSLT a un documento XML, eseguire la trasformazione e visualizzare l'output. L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.

 La proprietà **output** specifica il nome file per l'output. Se la proprietà **output** è vuota, nella directory temporanea viene generato un nome file. L'estensione del file è basata sull'elemento `xsl:output` del foglio di stile e può essere .xml, .txt o .htm.

 Se la proprietà **output** specifica un nome di file con estensione htm o HTML, l'output XSLT viene visualizzato in anteprima tramite [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Tutte le altre estensioni di file vengono aperte usando l'editor predefinito scelto da [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio. Ad esempio, se l'estensione del file è .xml, Visual Studio utilizzerà l'editor XML.

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Per eseguire una trasformazione XSLT da un documento XML

1. Aprire un documento XML nell'editor XML.

2. Associare un foglio di stile XSLT al documento XML.

    - Aggiungere un'istruzione di elaborazione `xml-stylesheet` al documento XML. Ad esempio, aggiungere la seguente riga `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` al prologo del documento.

         -oppure-

    - Aggiungere il foglio di stile XSLT utilizzando la finestra **Proprietà** . Nella **finestra Proprietà**del documento fare clic sul pulsante **Sfoglia** per il campo **foglio** di stile, selezionare il foglio di stile XSLT, quindi fare clic su **Apri**.

3. Fare clic sul pulsante **output ShowXSL** sulla barra degli strumenti dell' **editor XML** .

    > [!NOTE]
    > Se al documento XML non è associato alcun foglio di stile, viene visualizzata una finestra di dialogo con la richiesta di specificare il foglio di stile da usare.
    >
    >  L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Per eseguire una trasformazione XSLT da un foglio di stile XSLT

1. Aprire il foglio di stile XSLT nell'editor XML.

2. Specificare un documento XML nel campo di **input** della finestra **Proprietà** del documento.

    > [!NOTE]
    > Il documento XML è il documento di input usato per la trasformazione. Se un documento non viene specificato al momento dell'avvio della trasformazione XSLT, viene visualizzata la finestra di dialogo **Apri file** in cui è possibile specificare un documento.

3. Fare clic sul pulsante **output ShowXSLT** sulla barra degli strumenti dell' **editor XML** .

     L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.

### <a name="to-provide-a-different-output-file-name"></a>Per fornire un nome di file di output diverso

1. Specificare un nome di file nel campo **output** della finestra **Proprietà** del documento.

2. Fare clic sul pulsante **output ShowXSLT** sulla barra degli strumenti dell' **editor XML** .

     L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento e l'editor utilizzato nella finestra di output dipende dall'estensione di file della proprietà del documento di **output** .

## <a name="see-also"></a>Vedere anche
 [Editor XML](../xml-tools/xml-editor.md)
