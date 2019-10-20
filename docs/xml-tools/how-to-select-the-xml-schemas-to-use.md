---
title: 'Procedura: selezionare gli schemi XML da utilizzare'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275def786a93d42e6b8e110d3b3d785a24e948b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601904"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedura: selezionare gli schemi XML da utilizzare

L'editor XML fornisce una cache degli schemi situata nella directory *%VSInstallDir%\xml\Schemas* La cache degli schemi include schemi XML noti che vengono usati per IntelliSense e per la convalida di documenti XML.

Utilizzare la proprietà documento **schemi** per selezionare uno o più schemi di XML Schema Definition Language (XSD). È possibile selezionare gli schemi dalla cache degli schemi o altrove.

Gli schemi specificati vengono salvati in un file di opzioni utente della soluzione (nascosto) (. *suo*), insieme a tutte le altre proprietà dei documenti XML. Di conseguenza, non è necessario immettere nuovamente questi valori alla successiva apertura della soluzione.

> [!NOTE]
> L'editor può essere convalidato utilizzando uno schema inline o uno schema a cui fa riferimento l'attributo `xsd:schemaLocation`. Per ulteriori informazioni, vedere [convalida di documenti XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Per selezionare un XML Schema dalla cache degli schemi

1. Aprire un file nell'editor XML.

2. Nella finestra proprietà del documento fare clic nel campo **schemi** . Quando viene visualizzato il pulsante Sfoglia (...), fare clic su di esso.

   ![Proprietà Schemas per un file XML](media/properties-schemas.png)

   Verrà visualizzata la finestra di [dialogo schemi XML](xml-schemas-dialog-box.md) . Nella finestra di dialogo sono elencati tutti gli schemi con un. estensione *xsd* nella cache degli schemi (inclusi gli schemi a cui si fa riferimento nel file *Catalog. XML* ) e anche qualsiasi schema incluso nella soluzione corrente, aperto in Visual Studio, a cui si fa riferimento in un attributo `xsd:schemaLocation` o a cui si fa riferimento negli **schemi** Proprietà.

3. Selezionare gli schemi da usare per la convalida eseguendo una delle seguenti operazioni:

   - Selezionare uno schema elencato nella finestra di dialogo **schemi XML** , fare clic sulla colonna **utilizza** , quindi selezionare **utilizza questo schema**.

     oppure

   - Selezionare più schemi elencati nella finestra di dialogo **XML Schema** , quindi fare clic con il pulsante destro del mouse e scegliere **utilizza questo schema**.

4. Scegliere **OK**.

   L'elenco degli schemi selezionati viene nuovamente copiato nella proprietà del documento **schemas** .

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Per aggiungere un XML Schema alla cache degli schemi

1. Nella finestra proprietà del documento fare clic sul pulsante nel campo **schemi** .

2. Fare clic su **Aggiungi**.

   Verrà visualizzata la finestra di dialogo **Apri schema XSD** .

3. Individuare e selezionare gli schemi da aggiungere alla cache degli schemi.

4. Fare clic su **Apri**.

   Gli schemi vengono aggiunti alla cache dello schema e il valore della colonna **use** è impostato in modo da **utilizzare questo schema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Per eliminare un XML Schema dalla cache degli schemi

1. Nella finestra proprietà del documento fare clic sul pulsante nel campo **schemi** .

2. Selezionare lo schema da rimuovere e quindi fare clic su **Rimuovi**.

   Lo schema viene rimosso dalla cache degli schemi in memoria, ma non dal file system.

   > [!NOTE]
   > Se è ancora presente un riferimento allo schema tramite un attributo `schemaLocation` o un `targetNamespace` corrispondente, la **rimozione** non funzionerà in questa situazione a causa dell'associazione automatica. In questo caso è consigliabile contrassegnare lo schema come **non utilizzare gli schemi selezionati** nella colonna **utilizza** .

## <a name="see-also"></a>Vedere anche

- [Cache degli schemi](../xml-tools/schema-cache.md)
- [Finestra di dialogo schemi XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)