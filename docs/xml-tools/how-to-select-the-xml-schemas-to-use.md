---
title: 'Procedura: selezionare gli schemi XML da utilizzare'
description: Informazioni su come usare l'editor XML per selezionare uno schema XML dalla cache dello schema che include schemi XML noti usati per IntelliSense e la convalida di documenti XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 103be5fd5b18778eacb47d7bff10cd3c7107748e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114498"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedura: Selezionare gli SCHEMI XML da usare

L'editor XML fornisce una cache dello schema che si trova nella directory *%VSInstallDir%\xml\Schemas.* La cache degli schemi include schemi XML noti che vengono usati per IntelliSense e per la convalida di documenti XML.

Usare la **proprietà del documento** Schemi per selezionare uno o più schemi XSD (XML Schema Definition Language). È possibile selezionare gli schemi dalla cache dello schema o altrove.

Gli schemi specificati vengono salvati in un file di opzioni utente della soluzione (nascosto).*suo*), insieme a tutte le altre proprietà del documento XML. Di conseguenza, non è necessario reimportare questi valori alla successiva apertura della soluzione.

> [!NOTE]
> L'editor può eseguire la convalida usando uno schema inline o uno schema a cui fa riferimento `xsd:schemaLocation` l'attributo . Per altre informazioni, vedere [Convalida di documenti XML.](../xml-tools/xml-document-validation.md)

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Per selezionare uno schema XML dalla cache dello schema

1. Aprire un file nell'editor XML.

2. Nella finestra delle proprietà del documento fare clic nel **campo** Schemi. Quando viene visualizzato il pulsante Sfoglia (...) , fare clic su di esso.

   ![Proprietà Schemas per un file XML](media/properties-schemas.png)

   Verrà visualizzata la finestra di dialogo XML [Schemas](xml-schemas-dialog-box.md) . Nella finestra di dialogo sono elencati tutti gli schemi con un oggetto . Estensione *xsd* nella cache dello schema (inclusi gli schemi a cui viene fatto riferimento nel file *catalog.xml)* e anche qualsiasi schema presente nella soluzione corrente, aperto in Visual Studio, a cui si fa riferimento in un attributo o a cui si fa riferimento nella `xsd:schemaLocation` proprietà **Schemas.**

3. Selezionare gli schemi da usare per la convalida eseguendo una delle seguenti operazioni:

   - Selezionare uno schema elencato nella finestra **di dialogo XML Schemas** , fare clic sulla **colonna Use** (Usa) e quindi selezionare Use this **schema (Usa questo schema).**

     -oppure-

   - Selezionare più schemi elencati nella finestra **di dialogo XML Schema e** quindi fare clic con il pulsante destro del mouse e scegliere Usa questo **schema**.

4. Scegliere **OK**.

   L'elenco degli schemi selezionati viene copiato di nuovo nella **proprietà del documento** Schemi.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Per aggiungere uno schema XML alla cache dello schema

1. Nella finestra delle proprietà del documento fare clic sul pulsante nel **campo** Schemi.

2. Fare clic su **Aggiungi**.

   Verrà visualizzata la finestra di dialogo Apri **schema XSD.**

3. Individuare e selezionare gli schemi da aggiungere alla cache degli schemi.

4. Fare clic su **Apri**.

   Gli schemi vengono aggiunti alla cache dello schema e il **valore della** colonna Usa è impostato su Usa **questo schema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Per eliminare uno schema XML dalla cache dello schema

1. Nella finestra delle proprietà del documento fare clic sul pulsante nel **campo** Schemi.

2. Selezionare lo schema da rimuovere e quindi fare clic su **Rimuovi**.

   Lo schema viene rimosso dalla cache degli schemi in memoria, ma non dal file system.

   > [!NOTE]
   > Se si ha ancora un riferimento allo schema tramite un attributo o un elemento corrispondente, Remove non funzionerà in questa situazione a causa `schemaLocation` `targetNamespace` dell'associazione  automatica. In questo caso è consigliabile contrassegnare lo schema come Non **usare schemi selezionati** nella **colonna** Usa.

## <a name="see-also"></a>Vedi anche

- [Cache dello schema](../xml-tools/schema-cache.md)
- [Finestra di dialogo Xml Schemas](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)
