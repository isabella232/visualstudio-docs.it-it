---
title: 'Procedura: selezionare gli schemi XML da utilizzare'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d835a8592108b549a109f7bb7e128a8ae5b01611
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549103"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedura: selezionare gli schemi XML da usare

L'Editor XML fornisce una cache degli schemi situata nel *%InstallDir%\Xml\Schemas.* directory. La cache degli schemi include schemi XML noti che vengono usati per IntelliSense e per la convalida di documenti XML.

Il **schemi** proprietà del documento viene utilizzato per selezionare uno o più XML schema definition language (XSD) schemi da utilizzare. Consente di selezionare gli schemi dalla cache degli schemi o di specificare uno schema che non si trova nella cache.

Gli schemi specificati vengono salvati nel file di opzioni utente soluzione nascosto (. *suo*), insieme a tutti i dati XML di altre proprietà del documento. Di conseguenza non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.

> [!NOTE]
> L'editor può eseguire la convalida mediante uno schema inline o uno schema a cui fa riferimento l'attributo `xsd:schemaLocation`. Per altre informazioni, vedere [convalida di documenti XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Per selezionare uno schema XML dalla cache degli schemi

1.  Aprire un file nell'editor XML.

2.  Nella finestra delle proprietà del documento, scegliere il pulsante di **schemi** campo.

     Il **schemi XML** viene visualizzata la finestra di dialogo. Nella finestra di dialogo sono elencati tutti gli schemi con un. *xsd* estensione nella cache degli schemi (inclusi gli schemi a cui fa riferimento il *Catalog* file) e anche qualsiasi schema a cui nella soluzione corrente, aperta in Visual Studio, fa riferimento un `xsd:schemaLocation` attributo o a cui fa riferimento il **schemi** proprietà.

3.  Selezionare gli schemi da usare per la convalida eseguendo una delle seguenti operazioni:

    -   Selezionare uno schema elencato nella **schemi XML** finestra di dialogo, fare clic su di **utilizzare** colonna e quindi selezionare **utilizzano questo schema**.

     oppure

    -   Selezionare più schemi elencati nella **schemi XML** finestra di dialogo, fare clic e scegliere **utilizzano questo schema**.

4.  Fare clic su **OK**.

     L'elenco degli schemi selezionati verrà nuovamente copiata le **schemi** proprietà di documento.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Per aggiungere uno schema XML alla cache degli schemi

1.  Nella finestra delle proprietà del documento, scegliere il pulsante di **schemi** campo.

2.  Fare clic su **Aggiungi**.

     Verrà visualizzata la **Apri Schema XSD** finestra di dialogo.

3.  Individuare e selezionare gli schemi da aggiungere alla cache degli schemi.

4.  Fare clic su **aprire**.

     Gli schemi vengono aggiunti allo schema nella cache ed è il **utilizzare** il valore di colonna è impostato su **utilizzano questo schema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Per eliminare uno schema XML dalla cache degli schemi

1.  Nella finestra delle proprietà del documento, scegliere il pulsante di **schemi** campo.

2.  Selezionare lo schema da rimuovere e quindi fare clic su **rimuovere**.

     Lo schema viene rimosso dalla cache degli schemi in memoria, ma non dal file system.

    > [!NOTE]
    > Se si dispone ancora di un riferimento allo schema mediante un `schemaLocation` attributo o un corrispondente `targetNamespace` quindi **rimuovere** non funzioneranno in questa situazione, a causa dell'associazione automatica. In questo caso è consigliabile contrassegnare lo schema come **non utilizzano gli schemi selezionati** nel **utilizzare** colonna.

## <a name="see-also"></a>Vedere anche

- [Cache degli schemi](../xml-tools/schema-cache.md)
- [Finestra di dialogo schemi XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)