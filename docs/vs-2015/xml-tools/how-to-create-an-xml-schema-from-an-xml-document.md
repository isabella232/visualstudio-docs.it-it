---
title: 'Procedura: creare uno schema XML da un documento XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59e99320b122424e40da64b530bfe9a84a93eae1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670935"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedura: creare uno schema XML da un documento XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor XML consente di creare uno schema XSD (XML Schema Definition Language) da un documento XML. Il documento di istanza XML determina come viene generato lo schema nel seguente modo:

- Se al documento XML non è associato alcuno schema o DTD (Document Type Definition), i dati del documento XML vengono usati per inferire un nuovo schema XML.

- Se al documento XML è associata una DTD, la DTD esterna e il subset interno vengono convertiti in uno schema XML corrispondente.

- Se il documento XML contiene uno schema XDR (XML-Data Reduced) inline, lo schema XDR viene convertito in uno schema XML corrispondente.

  Gli schemi creati vengono quindi usati per fornire IntelliSense al documento XML.

  Per ulteriori informazioni sul motore di inferenza dello schema, vedere [deduzione di uno schema XML](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).

### <a name="to-create-an-xml-schema"></a>Per creare uno schema XML

1. Caricare un documento di istanza XML nell'editor XML.

2. Fare clic sul pulsante **Crea schema** dalla **barra degli strumenti**.

     Viene creato e aperto un documento di schema XML per ogni spazio dei nomi rilevato nel documento di istanza XML. Ogni schema viene aperto come file esterno temporaneo.

     Gli schemi possono essere salvati su disco, aggiunti al progetto oppure eliminati.

    > [!NOTE]
    > Il comando **Crea schema** è disponibile anche dal menu di scelta rapida dell'editor XML e dal menu **XML** .

## <a name="see-also"></a>Vedere anche
 [Editor XML](../xml-tools/xml-editor.md)
