---
title: 'Procedura: Selezionare gli schemi XML da usare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 385eee679c3a65db360d9ec6c0ab7735ff40128a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965493"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedura: Selezionare gli XML Schema da usare
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'editor XML fornisce una cache degli schemi situata nella directory %InstallDir%\Xml\Schemas. La cache degli schemi include schemi XML noti che vengono usati per IntelliSense e per la convalida di documenti XML.  
  
 Il **schemi** proprietà del documento viene usata per selezionare uno o più XML schema definition language (XSD) schemi da utilizzare. Consente di selezionare gli schemi dalla cache degli schemi o di specificare uno schema che non si trova nella cache.  
  
 Gli schemi specificati vengono salvati nel file nascosto SUO (Solution User Options) insieme a tutte le altre proprietà del documento XML. Di conseguenza non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.  
  
> [!NOTE]
>  L'editor può eseguire la convalida mediante uno schema inline o uno schema a cui fa riferimento l'attributo `xsd:schemaLocation`. Per altre informazioni, vedere [convalida dei documenti XML](../xml-tools/xml-document-validation.md).  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Per selezionare uno schema XML dalla cache degli schemi  
  
1. Aprire un file nell'editor XML.  
  
2. Nella finestra delle proprietà del documento, fare clic sul pulsante sul **schemi** campo.  
  
    Il **schemi XML** verrà visualizzata la finestra di dialogo. La finestra di dialogo elenca tutti gli schemi con estensione XSD nella cache degli schemi (inclusi gli schemi a cui fa riferimento il file Catalog XML) e anche qualsiasi schema a cui si trova nella soluzione corrente, aprire Visual Studio, a cui fa riferimento un `xsd:schemaLocation` o attributo, oppure a cui fa riferimento il **schemi** proprietà.  
  
3. Selezionare gli schemi da usare per la convalida eseguendo una delle seguenti operazioni:  
  
   - Selezionare uno schema elencato nella **schemi XML** finestra di dialogo, fare clic sul **utilizzare** colonna e quindi selezionare **utilizzano questo schema**.  
  
     -oppure-  
  
   - Selezionare più schemi elencati nella **schemi XML** finestra di dialogo, pulsante destro del mouse e scegliere **utilizzano questo schema**.  
  
4. Fare clic su **OK**.  
  
    L'elenco degli schemi selezionati viene copiato nuovamente il **schemi** proprietà del documento.  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Per aggiungere uno schema XML alla cache degli schemi  
  
1.  Nella finestra delle proprietà del documento, fare clic sul pulsante sul **schemi** campo.  
  
2.  Fare clic su **Aggiungi**.  
  
     Verrà visualizzata la **Apri Schema XSD** finestra di dialogo.  
  
3.  Individuare e selezionare gli schemi da aggiungere alla cache degli schemi.  
  
4.  Fare clic su **Apri**.  
  
     Gli schemi vengono aggiunti allo schema di memorizzare nella cache ed è il **utilizzo** il valore di colonna è impostato su **utilizzano questo schema**.  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Per eliminare uno schema XML dalla cache degli schemi  
  
1.  Nella finestra delle proprietà del documento, fare clic sul pulsante sul **schemi** campo.  
  
2.  Selezionare lo schema da rimuovere e quindi fare clic su **rimuovere**.  
  
     Lo schema viene rimosso dalla cache degli schemi in memoria, ma non dal file system.  
  
    > [!NOTE]
    >  Se ancora presente un riferimento allo schema mediante un `schemaLocation` un attributo o un oggetto corrispondente `targetNamespace` quindi **rimuovere** non funzionerà in questo caso a causa dell'associazione automatica. In questo caso, è consigliabile contrassegnare lo schema **non usare gli schemi selezionati** nel **utilizzare** colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Cache degli schemi](../xml-tools/schema-cache.md)   
 [Finestra di dialogo schemi XML](../xml-tools/xml-schemas-dialog-box.md)   
 [Editor XML](../xml-tools/xml-editor.md)
