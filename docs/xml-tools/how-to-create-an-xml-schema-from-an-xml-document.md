---
title: 'Procedura: creare uno schema XML da un documento XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f33fc5b48b9fd6b1cc08570e62e73f05fd19e70
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedura: creare uno schema XML da un documento XML

L'editor XML consente di creare uno schema XSD (XML Schema Definition Language) da un documento XML. Il documento di istanza XML determina come viene generato lo schema nel seguente modo:

-   Se al documento XML non è associato alcuno schema o DTD (Document Type Definition), i dati del documento XML vengono usati per inferire un nuovo schema XML.

-   Se al documento XML è associata una DTD, la DTD esterna e il subset interno vengono convertiti in uno schema XML corrispondente.

-   Se il documento XML contiene uno schema XDR (XML-Data Reduced) inline, lo schema XDR viene convertito in uno schema XML corrispondente.

Gli schemi creati vengono quindi usati per fornire IntelliSense al documento XML.

Per ulteriori informazioni sul motore di inferenza dello schema, vedere [deduzione di uno schema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Per creare uno schema XML

1.  Caricare un documento di istanza XML nell'editor XML.

2.  Fare clic su di **Create Schema** pulsante il **barra degli strumenti**.

     Viene creato e aperto un documento di schema XML per ogni spazio dei nomi rilevato nel documento di istanza XML. Ogni schema viene aperto come file esterno temporaneo.

     Gli schemi possono essere salvati su disco, aggiunti al progetto oppure eliminati.

    > [!NOTE]
    >  Il **Create Schema** comando è disponibile dal menu di scelta rapida dell'Editor XML e in anche il **XML** menu.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)