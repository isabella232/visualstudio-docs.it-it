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
ms.openlocfilehash: 41f830214b20df24587cf902e6b180e8a43a8cd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007397"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedura: Selezionare gli XML Schema da usare

L'editor XML fornisce una cache degli schemi situata nella *%VSInstallDir%\Xml\Schemas.* directory. La cache degli schemi include schemi XML noti che vengono usati per IntelliSense e per la convalida di documenti XML.

Usare la **schemi** proprietà per selezionare uno o più schemi XML schema definition language (XSD) del documento. È possibile selezionare gli schemi dalla cache degli schemi o altrove.

Gli schemi specificati vengono salvati in un file di opzioni utente (nascosto) soluzione (. *suo*), insieme a tutti gli altri XML nelle proprietà dei documenti. Di conseguenza, non è necessario immettere nuovamente tali valori alla successiva che apertura della soluzione.

> [!NOTE]
> L'editor è possibile convalidare mediante uno schema inline o uno schema fa riferimento il `xsd:schemaLocation` attributo. Per altre informazioni, vedere [convalida dei documenti XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Per selezionare uno schema XML dalla cache degli schemi

1. Aprire un file nell'editor XML.

2. Nella finestra delle proprietà del documento, fare clic nella **schemi** campo. Quando il pulsante Sfoglia (...) viene visualizzato, selezionarlo.

   ![Proprietà di schema per un file XML](media/properties-schemas.png)

   Il [finestra di dialogo schemi XML](xml-schemas-dialog-box.md) apre. La finestra di dialogo sono elencati tutti gli schemi con una. *xsd* estensione nella cache degli schemi (inclusi gli schemi a cui fa riferimento il *Catalog* file) e anche qualsiasi schema a cui nella soluzione corrente, aperta in Visual Studio, fa riferimento un `xsd:schemaLocation` attributo o a cui fa riferimento il **schemi** proprietà.

3. Selezionare gli schemi da usare per la convalida eseguendo una delle seguenti operazioni:

   - Selezionare uno schema elencato nella **schemi XML** finestra di dialogo, fare clic sul **utilizzare** colonna e quindi selezionare **utilizzano questo schema**.

     -oppure-

   - Selezionare più schemi elencati nella **schemi XML** finestra di dialogo e quindi fare clic e scegliere **utilizzano questo schema**.

4. Scegliere **OK**.

   L'elenco degli schemi selezionati viene copiato nuovamente il **schemi** proprietà del documento.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Per aggiungere un elemento XML schema alla cache degli schemi

1. Nella finestra delle proprietà del documento, fare clic sul pulsante sul **schemi** campo.

2. Fare clic su **Aggiungi**.

   Il **Apri Schema XSD** verrà visualizzata la finestra di dialogo.

3. Individuare e selezionare gli schemi da aggiungere alla cache degli schemi.

4. Fare clic su **Apri**.

   Gli schemi vengono aggiunti alla cache degli schemi e le **utilizzo** il valore di colonna è impostato su **utilizzano questo schema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Per eliminare uno schema XML dalla cache degli schemi

1. Nella finestra delle proprietà del documento, fare clic sul pulsante sul **schemi** campo.

2. Selezionare lo schema da rimuovere e quindi fare clic su **rimuovere**.

   Lo schema viene rimosso dalla cache degli schemi in memoria, ma non dal file system.

   > [!NOTE]
   > Se ancora presente un riferimento allo schema mediante un `schemaLocation` un attributo o un oggetto corrispondente `targetNamespace` quindi **rimuovere** non funzionerà in questo caso a causa dell'associazione automatica. In questo caso, è consigliabile contrassegnare lo schema **non usare gli schemi selezionati** nel **utilizzare** colonna.

## <a name="see-also"></a>Vedere anche

- [Cache degli schemi](../xml-tools/schema-cache.md)
- [Finestra di dialogo schemi XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)