---
title: 'Procedura: modificare i file XML | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac3864b3d3a3074f9b6be2529e8f674df90532c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245297"
---
# <a name="how-to-edit-xml-files"></a>Procedura: modificare i file XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'editor XML è il nuovo editor per file XML. Può essere usato per un file XML autonomo o per un file associato a un progetto Visual Studio. L'editor XML è associato alle estensioni di file seguenti: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt e .vssettings. L'editor XML è inoltre associato a qualsiasi altro tipo di file per il quale non è stato registrato un editor specifico e che presenta un contenuto XML o DTD.  
  
> [!NOTE]
>  I documenti XHTML sono gestiti dall'editor HTML.  
  
### <a name="to-edit-an-xml-file"></a>Per modificare un file XML  
  
1.  Fare doppio clic sul file che si desidera modificare.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>Per aggiungere un nuovo file XML a un progetto  
  
1.  Dal **Project** dal menu **Aggiungi nuovo elemento**.  
  
2.  Selezionare **File XML** dalle **modelli** riquadro.  
  
3.  Immettere il nome del file nei **Name** campo e premere **Add**.  
  
     Il file XML viene aggiunto al progetto e aperto nell'editor XML. Il file contiene la dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>Per aggiungere un file XML esistente a un progetto  
  
1.  Dal **Project** dal menu **Aggiungi elemento esistente**.  
  
     Il **Aggiungi elemento esistente** verrà visualizzata la finestra di dialogo.  
  
2.  Selezionare un file XML e premere **Add**.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>Per creare un nuovo file XML o XSLT  
  
1.  Dal **File** dal menu **New**.  
  
     Il **nuovo File** verrà visualizzata la finestra di dialogo.  
  
2.  Selezionare **File XML** per creare un nuovo file XML; o, selezionare **File XSLT** per creare un nuovo foglio di stile XSLT.  
  
3.  Fare clic su **aperto**.  
  
### <a name="to-create-a-project-for-xml-files"></a>Per creare un progetto per i file XML  
  
1.  Dal **File** dal menu **New**, quindi selezionare **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Selezionare il linguaggio del codice di propria scelta, seleziona **progetto vuoto**, fare clic su **OK**.  
  
3.  Aggiunta di file XML al progetto.  
  
     L'editor XML individua gli schemi aggiunti al progetto e li usa per la convalida e IntelliSense in qualsiasi file XML, schema o file XSLT che vengono modificati mentre il progetto è aperto.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)   
 [Proprietà di documento XML, finestra proprietà](../xml-tools/xml-document-properties-properties-window.md)   
 [Procedura: Creare uno schema XML da un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)



