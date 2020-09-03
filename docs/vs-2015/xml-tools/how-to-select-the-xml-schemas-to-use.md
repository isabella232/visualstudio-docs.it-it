---
title: 'Procedura: selezionare gli schemi XML da utilizzare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666511"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedura: selezionare gli schemi XML da utilizzare
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor XML fornisce una cache degli schemi situata nella directory %InstallDir%\Xml\Schemas. La cache degli schemi include schemi XML noti che vengono usati per IntelliSense e per la convalida di documenti XML.

 La proprietà del documento **schemas** viene utilizzata per selezionare uno o più schemi di XML Schema Definition Language (XSD) da utilizzare. Consente di selezionare gli schemi dalla cache degli schemi o di specificare uno schema che non si trova nella cache.

 Gli schemi specificati vengono salvati nel file nascosto SUO (Solution User Options) insieme a tutte le altre proprietà del documento XML. Di conseguenza non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.

> [!NOTE]
> L'editor può eseguire la convalida mediante uno schema inline o uno schema a cui fa riferimento l'attributo `xsd:schemaLocation`. Per ulteriori informazioni, vedere [convalida di documenti XML](../xml-tools/xml-document-validation.md).

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Per selezionare uno schema XML dalla cache degli schemi

1. Aprire un file nell'editor XML.

2. Nella finestra proprietà del documento fare clic sul pulsante nel campo **schemi** .

    Verrà visualizzata la finestra di dialogo **schemi XML** . Nella finestra di dialogo sono elencati tutti gli schemi con estensione xsd nella cache degli schemi (inclusi gli schemi a cui viene fatto riferimento nel file catalog.xml), nonché qualsiasi schema incluso nella soluzione corrente, aperto in Visual Studio, a cui si fa riferimento in un `xsd:schemaLocation` attributo o a cui si fa riferimento nella proprietà **schemas** .

3. Selezionare gli schemi da usare per la convalida eseguendo una delle seguenti operazioni:

   - Selezionare uno schema elencato nella finestra di dialogo **schemi XML** , fare clic sulla colonna **utilizza** , quindi selezionare **utilizza questo schema**.

     -oppure-

   - Selezionare più schemi elencati nella finestra di dialogo **XML Schema** , fare clic con il pulsante destro del mouse e selezionare **utilizza questo schema**.

4. Fare clic su **OK**.

    L'elenco degli schemi selezionati viene nuovamente copiato nella proprietà del documento **schemas** .

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Per aggiungere uno schema XML alla cache degli schemi

1. Nella finestra proprietà del documento fare clic sul pulsante nel campo **schemi** .

2. Scegliere **Aggiungi**.

     Verrà visualizzata la finestra di dialogo **Apri schema XSD** .

3. Individuare e selezionare gli schemi da aggiungere alla cache degli schemi.

4. Fare clic su **Apri**.

     Uno o più schemi aggiunti alla cache degli schemi e il valore della colonna **utilizza** è impostato su **utilizza questo schema**.

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Per eliminare uno schema XML dalla cache degli schemi

1. Nella finestra proprietà del documento fare clic sul pulsante nel campo **schemi** .

2. Selezionare lo schema da rimuovere e quindi fare clic su **Rimuovi**.

     Lo schema viene rimosso dalla cache degli schemi in memoria, ma non dal file system.

    > [!NOTE]
    > Se è ancora presente un riferimento allo schema tramite un `schemaLocation` attributo o un oggetto corrispondente, `targetNamespace` **Remove** non funzionerà in questa situazione a causa dell'associazione automatica. In questo caso è consigliabile contrassegnare lo schema come **non utilizzare gli schemi selezionati** nella colonna **utilizza** .

## <a name="see-also"></a>Vedere anche
 [Editor XML](../xml-tools/xml-editor.md) schema [della](../xml-tools/schema-cache.md) finestra di [dialogo schemi XML](../xml-tools/xml-schemas-dialog-box.md)
