---
title: 'Procedura: Selezionare gli XML Schema da usare'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 553fbc9bc8a96377a31864e1250987713714e147
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920561"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedura: Selezionare gli schemi XML da usare

L'Editor XML fornisce una cache degli schemi situata nella *%InstallDir%\Xml\Schemas.* directory. La cache degli schemi include schemi XML noti che vengono usati per IntelliSense e per la convalida di documenti XML.

Il **schemi** proprietà del documento viene usata per selezionare uno o più XML schema definition language (XSD) schemi da utilizzare. Consente di selezionare gli schemi dalla cache degli schemi o di specificare uno schema che non si trova nella cache.

Gli schemi specificati vengono salvati nel file delle opzioni utente nascosto soluzione (. *suo*), insieme a tutti gli altri XML nelle proprietà dei documenti. Di conseguenza non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.

> [!NOTE]
> L'editor può eseguire la convalida mediante uno schema inline o uno schema a cui fa riferimento l'attributo `xsd:schemaLocation`. Per altre informazioni, vedere [convalida dei documenti XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Per selezionare uno schema XML dalla cache degli schemi

1. Aprire un file nell'editor XML.

2. Nella finestra delle proprietà del documento, fare clic sul pulsante sul **schemi** campo.

    Il **schemi XML** verrà visualizzata la finestra di dialogo. La finestra di dialogo sono elencati tutti gli schemi con una. *xsd* estensione nella cache degli schemi (inclusi gli schemi a cui fa riferimento il *Catalog* file) e anche qualsiasi schema a cui nella soluzione corrente, aperta in Visual Studio, fa riferimento un `xsd:schemaLocation` attributo o a cui fa riferimento il **schemi** proprietà.

3. Selezionare gli schemi da usare per la convalida eseguendo una delle seguenti operazioni:

   - Selezionare uno schema elencato nella **schemi XML** finestra di dialogo, fare clic sul **utilizzare** colonna e quindi selezionare **utilizzano questo schema**.

     -oppure-

   - Selezionare più schemi elencati nella **schemi XML** finestra di dialogo, pulsante destro del mouse e scegliere **utilizzano questo schema**.

4. Fare clic su **OK**.

    L'elenco degli schemi selezionati viene copiato nuovamente il **schemi** proprietà del documento.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Per aggiungere un elemento XML schema alla cache degli schemi

1.  Nella finestra delle proprietà del documento, fare clic sul pulsante sul **schemi** campo.

2.  Fare clic su **Aggiungi**.

     Verrà visualizzata la **Apri Schema XSD** finestra di dialogo.

3.  Individuare e selezionare gli schemi da aggiungere alla cache degli schemi.

4.  Fare clic su **Apri**.

     Gli schemi vengono aggiunti allo schema di memorizzare nella cache ed è il **utilizzo** il valore di colonna è impostato su **utilizzano questo schema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Per eliminare uno schema XML dalla cache degli schemi

1.  Nella finestra delle proprietà del documento, fare clic sul pulsante sul **schemi** campo.

2.  Selezionare lo schema da rimuovere e quindi fare clic su **rimuovere**.

     Lo schema viene rimosso dalla cache degli schemi in memoria, ma non dal file system.

    > [!NOTE]
    > Se ancora presente un riferimento allo schema mediante un `schemaLocation` un attributo o un oggetto corrispondente `targetNamespace` quindi **rimuovere** non funzionerà in questo caso a causa dell'associazione automatica. In questo caso, è consigliabile contrassegnare lo schema **non usare gli schemi selezionati** nel **utilizzare** colonna.

## <a name="see-also"></a>Vedere anche

- [Cache degli schemi](../xml-tools/schema-cache.md)
- [Finestra di dialogo schemi XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)